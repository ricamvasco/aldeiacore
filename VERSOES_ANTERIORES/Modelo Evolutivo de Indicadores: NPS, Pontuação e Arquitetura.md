# Modelo Evolutivo de Indicadores: NPS, Pontuação e Arquitetura
**Autor:** Manus AI
**Data:** 08/05/2026

Este documento expande o sistema de indicadores da Aldeia, integrando a métrica de NPS (Net Promoter Score) nas três camadas de análise, detalhando a lógica matemática para promoção de terapeutas e definindo a arquitetura de banco de dados no Supabase para suportar a operação em tempo real.

---

## 1. O Sistema de NPS em 3 Camadas

O NPS (Net Promoter Score) mede a lealdade e satisfação através da pergunta: *"De 0 a 10, o quanto você recomendaria [X] para um amigo?"*. Na Aldeia, o NPS não é uma métrica única, mas um sistema tridimensional.

### 1.1. NPS da Clínica (Visão Global)
*   **O que mede:** A experiência geral da família com a Aldeia (infraestrutura, atendimento na recepção, facilidade de agendamento, faturamento).
*   **Quando é medido:** A cada 6 meses, enviado por e-mail/WhatsApp para toda a base ativa.
*   **Pergunta:** *"De 0 a 10, o quanto você recomendaria a Clínica Aldeia para outra família atípica?"*
*   **Meta:** > 85 (Zona de Excelência).

### 1.2. NPS da Área de Especialização (Visão Tática)
*   **O que mede:** A percepção de valor e eficácia de uma especialidade específica (ex: "A Fonoaudiologia da Aldeia é boa?").
*   **Quando é medido:** Trimestralmente, segmentado por pacientes que utilizam o serviço.
*   **Pergunta:** *"De 0 a 10, como você avalia o impacto das terapias de [Fonoaudiologia] no desenvolvimento do seu filho?"*
*   **Meta:** > 80.

### 1.3. NPS do Terapeuta (Visão Individual)
*   **O que mede:** O vínculo terapêutico, a confiança da família no profissional e a clareza na comunicação (Parent Training).
*   **Quando é medido:** No 3º mês de atendimento (NPS de Onboarding) e depois a cada 6 meses.
*   **Pergunta:** *"De 0 a 10, o quanto você confia no trabalho do terapeuta [Nome] para o desenvolvimento do seu filho?"*
*   **Meta:** > 90 (O vínculo direto costuma ter notas mais altas que a clínica como um todo).

---

## 2. Lógica de Pontuação para Promoção (Avaliação de Desempenho)

A promoção na "Jornada de Crescimento Sistêmico" (da Semente à Árvore) não é baseada em tempo de casa, mas em uma **pontuação trimestral de 0 a 100 pontos**.

### 2.1. A Fórmula de Pontuação (Os 3 Pilares)

A nota final do terapeuta é a soma de três pilares:

**Pilar 1: Desempenho Clínico (Máximo 40 pontos)**
*   Evolução do Paciente (atingimento de metas do plano): 15 pts
*   Qualidade Técnica (aplicação de protocolos): 10 pts
*   **NPS do Terapeuta (Satisfação da Família): 10 pts**
*   Visão Transdisciplinar (participação em reuniões de caso): 5 pts

**Pilar 2: Desempenho Operacional (Máximo 30 pontos)**
*   Prontuários em 24h: 15 pts
*   Pontualidade/Assiduidade: 10 pts
*   Cuidado com o espaço: 5 pts

**Pilar 3: Fit Cultural e Soft Skills (Máximo 30 pontos)**
*   Inteligência Emocional: 10 pts
*   Trabalho em Equipe: 10 pts
*   Postura de Aprendiz: 10 pts

### 2.2. A Régua de Promoção por Nível

Como a exigência técnica aumenta a cada nível, a **pontuação mínima exigida para ser promovido também aumenta**.

| Nível Atual | Cargo | Pontuação Mínima para Permanecer | Pontuação Mínima para Promoção |
| :--- | :--- | :---: | :---: |
| 🌱 **Semente** | Estagiário | 60 pontos | **80 pontos** |
| 🌿 **Broto** | Assistente Terapêutico | 65 pontos | **85 pontos** |
| 🪵 **Caule** | Terapeuta Júnior | 70 pontos | **85 pontos** |
| 🌾 **Ramo** | Terapeuta Pleno | 75 pontos | **90 pontos** |
| 🍃 **Folha** | Terapeuta Sênior | 80 pontos | **95 pontos** |
| 🍎 **Fruto** | Especialista | 85 pontos | **95 pontos** |
| 🌳 **Árvore** | Mentor / Diretor | 90 pontos | N/A (Topo) |

*Exemplo prático:* Um Terapeuta Júnior (Caule) tira 82 pontos na avaliação. Ele está acima do mínimo para permanecer (70), mas abaixo do mínimo para ser promovido a Pleno (85). Ele continua como Júnior no próximo trimestre.

### 2.3. O Gatilho Financeiro (A Trava de Segurança)
Mesmo que o terapeuta atinja a pontuação para promoção, ela só é efetivada se a clínica estiver com **EBITDA positivo**. Se a clínica estiver no vermelho, o terapeuta entra na "Fila de Promoção Prioritária" para o próximo ciclo financeiro positivo.

---

## 3. Arquitetura de Banco de Dados (Supabase)

Para que os dashboards funcionem em tempo real e cada usuário veja apenas o que lhe compete, utilizaremos o **Supabase (PostgreSQL)** com **Row-Level Security (RLS)** [1].

### 3.1. Estrutura de Tabelas (Schema)

Abaixo, o modelo relacional simplificado para suportar os KPIs e as avaliações:

**1. Tabela `users` (Usuários do Sistema)**
*   `id` (UUID, Primary Key)
*   `role` (Enum: 'admin', 'lider_area', 'terapeuta')
*   `nivel_carreira` (Enum: 'semente', 'broto', 'caule', etc.)
*   `area_id` (Foreign Key para tabela `areas`)

**2. Tabela `sessoes` (Atendimentos)**
*   `id` (UUID)
*   `terapeuta_id` (Foreign Key para `users`)
*   `paciente_id` (UUID)
*   `data_hora` (Timestamp)
*   `status` (Enum: 'realizada', 'falta_paciente', 'falta_terapeuta')
*   `prontuario_preenchido_em` (Timestamp - para calcular o SLA de 24h)

**3. Tabela `nps_respostas` (Pesquisas de Satisfação)**
*   `id` (UUID)
*   `tipo_nps` (Enum: 'clinica', 'area', 'terapeuta')
*   `alvo_id` (UUID - pode ser o ID da clínica, da área ou do terapeuta)
*   `nota` (Integer 0-10)
*   `comentario` (Text)
*   `data_resposta` (Timestamp)

**4. Tabela `avaliacoes_desempenho` (Scoring Trimestral)**
*   `id` (UUID)
*   `terapeuta_id` (Foreign Key para `users`)
*   `trimestre` (String, ex: '2026-Q3')
*   `nota_clinica` (Integer 0-40)
*   `nota_operacional` (Integer 0-30)
*   `nota_cultural` (Integer 0-30)
*   `nota_total` (Integer 0-100)
*   `elegivel_promocao` (Boolean)

### 3.2. A Mágica do Row-Level Security (RLS)

O RLS é uma política de segurança configurada direto no banco de dados [2]. É ele que garante que o dashboard do terapeuta só mostre os dados dele.

**Exemplo de Política RLS na tabela `sessoes`:**
```sql
-- O terapeuta só pode ver as sessões onde ele é o terapeuta_id
CREATE POLICY "Terapeutas veem apenas suas sessões"
ON sessoes FOR SELECT
USING (auth.uid() = terapeuta_id);

-- O líder de área pode ver as sessões de todos os terapeutas da sua área
CREATE POLICY "Líderes veem sessões da sua área"
ON sessoes FOR SELECT
USING (
  EXISTS (
    SELECT 1 FROM users u
    WHERE u.id = auth.uid() AND u.role = 'lider_area' AND u.area_id = sessoes.area_id
  )
);

-- Admins (Sócios) veem tudo
CREATE POLICY "Admins veem tudo"
ON sessoes FOR SELECT
USING (
  EXISTS (
    SELECT 1 FROM users WHERE id = auth.uid() AND role = 'admin'
  )
);
```

### 3.3. Próximos Passos para Implementação

1.  **Criar o Projeto no Supabase:** Abrir uma conta gratuita, criar o projeto "Aldeia-Core" e rodar os scripts SQL para criar as tabelas acima.
2.  **Configurar o RLS:** Aplicar as políticas de segurança para garantir o isolamento dos dados.
3.  **Conectar o Retool (ou Appsmith):** Ligar a ferramenta de dashboard ao Supabase e criar as três telas (Visão Sócio, Visão Líder, Visão Terapeuta).
4.  **Definir a Ingestão de Dados:** Decidir se os dados das sessões virão via API do software de gestão (ex: Feegow) ou se serão inseridos manualmente no início da operação.

---

## Referências

[1] Supabase. Role-Based Access Control (RBAC). Disponível em: https://supabase.com/features/role-based-access-control
[2] Supabase. Building Role-Based Access Control (RBAC) with Supabase Row-Level Security. Disponível em: https://medium.com/@lakshaykapoor08/building-role-based-access-control-rbac-with-supabase-row-level-security-c82eb1865dfd
