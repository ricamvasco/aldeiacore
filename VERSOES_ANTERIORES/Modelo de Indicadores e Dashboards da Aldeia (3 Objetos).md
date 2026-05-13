# Modelo de Indicadores e Dashboards da Aldeia (3 Objetos)
**Autor:** Manus AI
**Data:** 08/05/2026

Este documento estrutura o sistema de indicadores (KPIs) da Aldeia em três camadas interdependentes: **Clínica, Áreas de Especialização e Terapeuta**. Além disso, detalha a arquitetura técnica recomendada para implementar dashboards em tempo real com controle de acesso por perfil de usuário.

---

## 1. Estrutura de Indicadores (Os 3 Objetos)

A lógica do sistema é "top-down" para a estratégia e "bottom-up" para a execução. O desempenho do terapeuta alimenta o resultado da área, que por sua vez sustenta a saúde da clínica.

### Objeto 1: A Clínica (Visão Executiva)
**Público-alvo:** Sócios (Rica e Letícia)
**Objetivo:** Monitorar a saúde financeira, o crescimento e a sustentabilidade do negócio.

| Indicador (KPI) | O que mede | Meta / Alvo | Frequência |
|---|---|---|---|
| **Faturamento Bruto** | Receita total gerada no mês | R$ 63.000 (Breakeven) | Diário/Mensal |
| **Sessões Realizadas** | Volume total de atendimentos | 420 sessões/mês | Diário/Mensal |
| **Taxa de Ocupação Global** | (Horários Ocupados / Horários Disponíveis) | 70% | Semanal |
| **Ticket Médio por Sessão** | (Faturamento / Sessões Realizadas) | R$ 150,00 | Mensal |
| **Taxa de Inadimplência** | % de faturas não pagas no vencimento | < 5% | Semanal |
| **NPS Global (Famílias)** | Satisfação geral com a clínica | > 85 | Trimestral |
| **Turnover da Equipe** | Taxa de rotatividade de terapeutas | < 10% ao ano | Semestral |

### Objeto 2: Áreas de Especialização (Visão Tática)
**Público-alvo:** Sócios e Líderes de Área (Nível Árvore/Fruto)
**Objetivo:** Entender qual especialidade (Psicologia, Fonoaudiologia, T.O., etc.) está tracionando a clínica e qual precisa de apoio.

| Indicador (KPI) | O que mede | Meta / Alvo | Frequência |
|---|---|---|---|
| **Ocupação por Área** | % de agenda preenchida na especialidade | > 75% | Semanal |
| **Fila de Espera (Demanda Reprimida)** | Número de pacientes aguardando vaga na área | Zero (indica necessidade de contratação) | Semanal |
| **Taxa de Conversão de Avaliação** | % de avaliações que viram plano terapêutico | > 80% | Mensal |
| **LTV (Lifetime Value) Médio da Área** | Tempo médio que o paciente fica na terapia | > 18 meses | Semestral |
| **Margem de Contribuição da Área** | (Receita da Área - Repasses da Área) | > 60% | Mensal |

### Objeto 3: O Terapeuta (Visão Operacional e Carreira)
**Público-alvo:** O próprio Terapeuta e seu Mentor
**Objetivo:** Guiar a progressão na "Jornada de Crescimento Sistêmico" (dos níveis Semente a Árvore) e garantir a qualidade clínica.

| Indicador (KPI) | O que mede | Meta / Alvo | Frequência |
|---|---|---|---|
| **Taxa de Ocupação Individual** | % da agenda do terapeuta preenchida | > 80% | Semanal |
| **Assiduidade e Pontualidade** | % de sessões iniciadas no horário | > 95% | Mensal |
| **Precisão de Registros (SLA 24h)** | % de prontuários preenchidos em até 24h | 100% | Semanal |
| **Taxa de Retenção de Pacientes** | % de pacientes que não abandonam o tratamento | > 90% | Trimestral |
| **Evolução Clínica (Protocolos)** | % de pacientes atingindo marcos do plano | > 70% | Trimestral |
| **Horas de Capacitação** | Horas dedicadas a cursos e supervisão | > 4h/mês | Mensal |

---

## 2. Solução Técnica: Dashboards em Tempo Real com Controle de Acesso

Para que cada colaborador acesse **apenas os dados pertinentes ao seu perfil** (ex: o terapeuta só vê seus próprios números, o líder vê sua área, os sócios veem tudo), precisamos de uma arquitetura que suporte **Row-Level Security (RLS)** ou controle de acesso baseado em função (RBAC) [1] [2].

### A Arquitetura Recomendada (Custo-Benefício para a Aldeia)

Para o momento atual (pré-inauguração e primeiro ano), a solução mais inteligente, barata e escalável é a combinação de **Supabase + Retool** ou **Google Sheets + Looker Studio**.

#### Opção A: A Solução Profissional (Recomendada)
**Banco de Dados:** Supabase (PostgreSQL)
**Dashboard/Interface:** Retool ou Appsmith

* **Como funciona:** O Supabase armazena os dados e possui RLS (Row-Level Security) nativo [3]. O Retool cria a interface visual (o "app" da clínica).
* **Acesso por Perfil:**
    * **Terapeuta (Login A):** O banco de dados filtra automaticamente e o dashboard só mostra os KPIs individuais dele.
    * **Líder de Área (Login B):** O dashboard mostra os KPIs agregados da Fonoaudiologia, por exemplo.
    * **Sócios (Login C):** Acesso irrestrito a todos os painéis.
* **Custo:** Supabase (Grátis até 500MB) + Retool (Grátis para até 5 usuários, depois ~$10/usuário/mês).

#### Opção B: A Solução "No-Code" Rápida (Alternativa)
**Banco de Dados:** Google Sheets
**Dashboard:** Google Looker Studio

* **Como funciona:** Os dados ficam em planilhas. O Looker Studio lê as planilhas e gera os gráficos.
* **Acesso por Perfil:** O Looker Studio permite configurar "Filtros de E-mail" (Row-Level Security básico) [4]. Quando o terapeuta `joao@aldeia.com` acessa o link do dashboard, o Google filtra a planilha e só mostra as linhas onde o e-mail é o dele.
* **Custo:** 100% Gratuito.
* **Ponto de Atenção:** É mais frágil que a Opção A. Se a planilha quebrar, o dashboard cai. Não é um sistema de gestão real, é apenas visualização.

### 3. Como Implementar na Prática

1. **Fase 1 (Agora - Pré-inauguração):** Estruturar a coleta de dados. Como os agendamentos e prontuários serão registrados? Se for via software de terceiros (ex: Feegow, Clínica Ágil), precisamos verificar se eles exportam dados via API.
2. **Fase 2 (Mês 1 a 3):** Construir a Opção B (Google Sheets + Looker Studio) para validar quais indicadores realmente importam no dia a dia, sem gastar dinheiro.
3. **Fase 3 (Mês 6+):** Migrar para a Opção A (Supabase + Retool) construindo um portal interno da Aldeia, onde o terapeuta faz login, vê sua agenda, seus KPIs e seu extrato de repasses no mesmo lugar.

---

## Referências

[1] Retool. Configure role-based access control - Permissions. Disponível em: https://docs.retool.com/permissions/guides/roles-permissions
[2] Supabase. Role-Based Access Control (RBAC). Disponível em: https://supabase.com/features/role-based-access-control
[3] Supabase. Building Role-Based Access Control (RBAC) with Supabase Row-Level Security. Disponível em: https://medium.com/@lakshaykapoor08/building-role-based-access-control-rbac-with-supabase-row-level-security-c82eb1865dfd
[4] Google Cloud. Implementing row-level segmentation for embedded Looker content. Disponível em: https://docs.cloud.google.com/looker/docs/implementing-row-level-segmentation-in-embeds
