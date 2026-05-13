# Mapeamento Completo da Plataforma Aldeia

**Documento de Produto | Versão 1.0 | Maio 2026**

---

## Visão Geral

A Plataforma Aldeia é o sistema único de gestão da Clínica Aldeia, projetado para substituir integralmente ferramentas como iClinic e Neo ABA. O sistema deve cobrir todas as necessidades operacionais, clínicas, financeiras e de comunicação da clínica multidisciplinar de atendimento a crianças com TEA.

Este documento mapeia **todos os módulos necessários**, indicando o que já foi implementado, o que precisa ser evoluído e o que precisa ser criado do zero. A organização segue a mesma estrutura de grupos da sidebar do dashboard.

---

## Status Consolidado

| Categoria | Implementado | A Evoluir | A Criar | Total |
|-----------|:---:|:---:|:---:|:---:|
| Visão Geral | 3 | 1 | 0 | 4 |
| Clínico | 3 | 3 | 4 | 10 |
| Financeiro | 3 | 2 | 2 | 7 |
| Comunicação | 4 | 1 | 2 | 7 |
| Relatórios | 2 | 1 | 2 | 5 |
| Administrativo | 5 | 1 | 3 | 9 |
| Portal Externo | 2 | 1 | 1 | 4 |
| **TOTAL** | **22** | **10** | **14** | **46** |

---

## Módulo 1: Visão Geral (Dashboards)

Este módulo concentra os painéis de indicadores para cada perfil de usuário. Cada dashboard deve apresentar KPIs relevantes ao papel do profissional, com dados reais do banco.

| Funcionalidade | Status | Observações |
|---|---|---|
| Dashboard Executivo (Sócios) | Implementado | Precisa conectar a dados reais quando clínica abrir |
| Dashboard por Área (Líderes) | Implementado | Dados demo — conectar ao banco |
| Dashboard do Terapeuta | Implementado | Dados demo — conectar ao banco |
| Dashboard de Crescimento | A Criar | Métricas de captação, retenção, churn, LTV por paciente |

**Evolução necessária:** Todos os dashboards existentes operam com dados demonstrativos. Quando a clínica iniciar operação, as queries devem ser substituídas por consultas reais ao banco de dados, refletindo sessões, NPS, faturamento e produtividade em tempo real.

---

## Módulo 2: Clínico

O módulo clínico é o coração da operação terapêutica. Baseado na análise dos vídeos da Letícia, este módulo precisa de evolução significativa para atender aos requisitos de qualidade clínica, conformidade legal e eficiência operacional.

| Funcionalidade | Status | Observações |
|---|---|---|
| Prontuário Digital | Evoluir | Refatorar: campos estruturados (estado geral, objetivo, respostas). Texto livre apenas para "respostas do paciente" |
| Registro de Sessões | Implementado | Funcional com CRUD, filtros e calendário |
| Agenda Visual (Agendamento) | Implementado | Calendário semanal com blocos por área |
| Gestão de Metas Terapêuticas | Evoluir | Conectar metas à evolução. Adicionar campo qualitativo além de Sim/Não. Integrar protocolos (VB-MAPP, Denver, ABLLS-R) |
| Protocolos Clínicos Integrados | A Criar | VB-MAPP, Denver, ABLLS-R com marcos e gráficos de progresso |
| Gestão de Guias/Convênios | A Criar | PRIORIDADE CRÍTICA. Cadastro de guias, alertas de vencimento, bloqueio pré-atendimento, fluxo de renovação |
| Jornada do Paciente no Dia | A Criar | Visualização de quem atende o paciente antes e depois na mesma data |
| Perfil Clínico Completo | Evoluir | Diagnóstico, comorbidades e medicação OBRIGATÓRIOS. Editável por terapeutas com log de alterações |
| Assinatura Digital | A Criar | Feedback aos pais com assinatura digital (touch/mouse). Eliminar processo analógico |
| Lista de Espera | A Criar | Fila de pacientes aguardando vaga com priorização automática |

**Detalhamento — Gestão de Guias (Prioridade Crítica):**

A gestão de guias é o problema mais urgente identificado nos vídeos. O sistema deve cadastrar guias por paciente com número de autorização, data de validade e plano de saúde. Alertas automáticos devem ser disparados 30, 15 e 7 dias antes do vencimento — tanto para os pais (via WhatsApp e Portal) quanto para a administração (via painel). Antes de cada atendimento, o sistema deve verificar se a guia está válida e bloquear o registro de evolução caso contrário, exibindo um alerta claro ao terapeuta. O fluxo de renovação deve incluir um checklist guiado para os pais (agendar médico → pegar encaminhamento → entregar na recepção → recepção solicita nova guia).

**Detalhamento — Evolução Estruturada:**

O prontuário deve ser refatorado para conter campos fechados que permitam extração automática de dados. A estrutura proposta é: (1) Estado geral do paciente via checkboxes (adequado, irritado, sonolento, agitado, colaborativo); (2) Objetivo da terapia vinculado às metas ativas do paciente via select; (3) Metas trabalhadas na sessão com marcação Sim/Não + campo qualitativo; (4) Respostas do paciente em texto livre (único campo aberto); (5) Observações adicionais (opcional). A especialidade do terapeuta deve ser auto-preenchida com base no perfil logado.

---

## Módulo 3: Financeiro

O módulo financeiro deve suportar dois modelos de remuneração: por sessão (padrão) e por hora (modelo da Letícia, R$ 120/hora). O comissionamento deve considerar o plano de carreira de 7 níveis (Semente 30% → Árvore 60%).

| Funcionalidade | Status | Observações |
|---|---|---|
| Dashboard Financeiro (DRE) | Implementado | Receita, despesas, lucro, fluxo de caixa |
| Contas a Receber | Implementado | Pagamentos por paciente, inadimplência |
| Contas a Pagar | Implementado | Salários, aluguel, fornecedores |
| Comissionamento Automático | Evoluir | Adicionar modelo por HORA além de por sessão. Vincular ao plano de carreira (7 níveis) |
| Simulador de Ganhos | Evoluir | Adicionar modelo por hora. Terapeuta escolhe seu modelo de remuneração |
| Faturamento por Convênio | A Criar | Controle de quanto cada convênio deve à clínica, com status de pagamento e glosas |
| Projeção de Faturamento | A Criar | Baseado na agenda futura (sessões agendadas × valor) vs. meta mensal |

**Detalhamento — Modelo por Hora:**

Alguns terapeutas (como a Letícia) recebem por hora trabalhada, não por sessão realizada. O sistema deve permitir configurar o modelo de remuneração no perfil do terapeuta (por sessão ou por hora), registrar horas trabalhadas automaticamente com base na agenda, e calcular o comissionamento de acordo. O simulador de ganhos deve suportar ambos os modelos para que o terapeuta projete seus rendimentos corretamente.

---

## Módulo 4: Comunicação

O módulo de comunicação gerencia toda a interação com famílias, equipe interna e sistemas externos de mensageria.

| Funcionalidade | Status | Observações |
|---|---|---|
| WhatsApp NPS (Envio automático) | Implementado | Pronto para credenciais Meta Business |
| WhatsApp Métricas | Implementado | Dashboard de engajamento |
| NPS Público (Formulário) | Implementado | Rota pública /nps |
| Notificações Push | Implementado | Alertas para sócios (NPS, faltas, metas) |
| Central de Mensagens | A Criar | Envio de comunicados para famílias (feriados, mudanças de horário, eventos). Templates reutilizáveis |
| Notificações Multicanal para Guias | A Criar | Alertas de vencimento via WhatsApp + Portal + Painel Admin |
| Notificações para Terapeutas | Evoluir | Alertas de guia inválida antes do atendimento, lembretes de prontuário pendente |

**Detalhamento — Central de Mensagens:**

A clínica precisa de um canal unificado para comunicar-se com todas as famílias simultaneamente ou por segmento (área, terapeuta, turno). Funcionalidades: templates de mensagem reutilizáveis, agendamento de envio, segmentação por grupo, histórico de comunicações por família, e integração com WhatsApp Business API para envio em massa.

---

## Módulo 5: Relatórios

O módulo de relatórios deve eliminar completamente a necessidade de exportar dados para Excel. Relatórios para convênios devem ser gerados automaticamente no formato exigido por cada operadora.

| Funcionalidade | Status | Observações |
|---|---|---|
| Relatórios PDF (Gerencial) | Implementado | KPIs, desempenho por área, top terapeutas |
| Produtividade por Terapeuta | Implementado | Ranking, ocupação, destaques/alertas |
| Relatório para Convênios | A Criar | PRIORIDADE ALTA. Geração automática no formato FUSEX, Unimed, etc. Sem exportar para Excel |
| Relatório de Evolução do Paciente | A Criar | Compilação das evoluções estruturadas por período, para entregar aos pais ou convênios |
| Exportação iCal | Implementado | Endpoint /api/calendar/feed funcionando |

**Detalhamento — Relatório para Convênios:**

Cada convênio exige um formato específico de relatório. O sistema deve ter templates configuráveis por operadora (FUSEX, Unimed, etc.) que extraem automaticamente dos campos estruturados da evolução: objetivo da terapia, metas trabalhadas, respostas do paciente e progresso. O terapeuta seleciona o período e o paciente, e o sistema gera o documento pronto para envio — sem intermediação manual em planilhas.

---

## Módulo 6: Administrativo

O módulo administrativo cobre a gestão de pessoas, espaço físico, configurações e processos internos.

| Funcionalidade | Status | Observações |
|---|---|---|
| Cadastro de Colaboradores | Implementado | CRUD de terapeutas com perfil |
| Cadastro de Pacientes | Implementado | Conectado ao banco via tRPC |
| Gestão de Salas | Implementado | Mapa visual com ocupação |
| Onboarding de Terapeutas | Implementado | Stepper de 5 etapas |
| Metas Editáveis | Implementado | Progresso visual, filtros por tipo/área |
| Painel Admin | Evoluir | Adicionar gestão de permissões por perfil (sócio, líder, terapeuta, recepção) |
| Gestão de Permissões | A Criar | Controle granular: quem pode editar perfil clínico, quem pode ver financeiro, quem pode registrar evolução |
| Gestão de Anexos/Documentos | A Criar | Upload com metadados automáticos (data, autor, tipo). Busca por categoria. Organização por paciente |
| Checklist de Abertura | A Criar | Tarefas pré-abertura com status, responsável e prazo |

**Detalhamento — Gestão de Permissões:**

O sistema atual da Letícia não permite que terapeutas editem informações clínicas do paciente, o que gera perfis vazios. A Aldeia deve ter um sistema de permissões granular onde cada perfil (sócio, líder de área, terapeuta, recepção) tenha acessos específicos. Terapeutas devem poder editar informações clínicas dos seus pacientes, mas não dados financeiros. A recepção deve poder cadastrar pacientes e guias, mas não acessar prontuários. Sócios têm acesso total.

---

## Módulo 7: Portal Externo (Famílias e Público)

O portal externo é a interface da clínica com o mundo exterior — famílias dos pacientes e público em geral.

| Funcionalidade | Status | Observações |
|---|---|---|
| Portal da Família | Implementado | Timeline de evoluções, sistema de níveis |
| QR Code NPS | Implementado | Geração personalizada com presets |
| Portal com Autenticação por Token | Evoluir | Gerar tokens únicos por paciente. Família acessa /portal-familia?token=xxx |
| Área de Agendamento para Pais | A Criar | Pais visualizam próximas sessões, solicitam remarcação, recebem confirmação |

**Detalhamento — Portal da Família Completo:**

O portal deve ser o principal canal de transparência com as famílias. Cada família recebe um link único (token) que dá acesso a: (1) Próximas sessões agendadas com horário e terapeuta; (2) Histórico de evoluções com resumo por sessão; (3) Progresso nas metas terapêuticas com gráficos visuais; (4) Feedbacks dos terapeutas com assinatura digital; (5) Alertas de guia próxima do vencimento com instruções de renovação; (6) Canal para solicitar remarcação de sessão.

---

## Módulo 8: Inteligência Artificial (Integrado)

Funcionalidades de IA que rodam dentro do sistema para auxiliar terapeutas e gestores no dia a dia.

| Funcionalidade | Status | Observações |
|---|---|---|
| Gerar Resumo de Evolução | A Criar | IA gera texto profissional a partir dos campos estruturados preenchidos |
| Sugerir Plano Terapêutico | A Criar | Baseado no diagnóstico, protocolo e progresso nas metas |
| Análise de Tendências | A Criar | Identificar padrões nos dados (queda de NPS, aumento de faltas, estagnação de metas) |
| FAQ Automático WhatsApp | A Criar | Responder perguntas frequentes das famílias automaticamente |
| Transcrição de Sessões | A Criar | Whisper para transcrever áudios de supervisão ou reuniões |

**Detalhamento — IA no Prontuário:**

Após o terapeuta preencher os campos estruturados da evolução (estado geral, objetivo, metas, respostas), o sistema oferece um botão "Gerar resumo com IA" que produz um texto narrativo profissional combinando todos os dados. O terapeuta revisa, edita se necessário, e salva. Isso economiza 5-10 minutos por sessão e garante qualidade uniforme nos registros — especialmente útil para relatórios de convênio.

---

## Roadmap de Implementação

A implementação segue uma lógica de prioridade baseada em impacto operacional e financeiro.

| Sprint | Foco | Funcionalidades | Prazo Estimado |
|--------|------|-----------------|----------------|
| **1** | Guias + Alertas | Gestão de Guias, Alertas de Vencimento, Bloqueio pré-atendimento | 1 semana |
| **2** | Evolução Estruturada | Prontuário com campos fechados, Metas conectadas, Auto-preenchimento | 1 semana |
| **3** | Relatórios Convênio + Assinatura | Templates por operadora, Geração automática, Assinatura digital | 1 semana |
| **4** | Perfil Completo + Permissões | Perfil clínico obrigatório, Gestão de permissões, Jornada do dia | 1 semana |
| **5** | Financeiro por Hora + Projeção | Modelo por hora, Faturamento por convênio, Projeção de faturamento | 3-4 dias |
| **6** | Portal Família Completo | Autenticação por token, Área de agendamento, Alertas de guia | 1 semana |
| **7** | Comunicação Avançada | Central de mensagens, Notificações multicanal, Templates | 3-4 dias |
| **8** | IA Integrada | Resumo de evolução, Sugestão de plano, Análise de tendências | 1 semana |
| **9** | Protocolos + Lista de Espera | VB-MAPP, Denver, ABLLS-R integrados, Fila de espera | 1 semana |
| **10** | Polimento + Dados Reais | Conectar dashboards ao banco, Seed de dados, Testes E2E | 3-4 dias |

---

## Decisões de Negócio Registradas

Estas são decisões já tomadas que devem ser respeitadas em toda a implementação:

1. **Não usar sistemas externos** — iClinic e Neo ABA estão descartados. A plataforma Aldeia é o sistema único.
2. **Plano de carreira com 7 níveis** — Semente (30%), Broto (35%), Caule (40%), Ramo (45%), Folha (50%), Fruto (55%), Árvore (60%).
3. **Dois modelos de remuneração** — por sessão (padrão) e por hora (R$ 120/hora para alguns terapeutas).
4. **Evolução retroativa é PROIBIDA** — integridade do registro é inegociável. Sistema deve impedir.
5. **Convênios atendidos** — FUSEX, Unimed (pelo menos).
6. **Protocolos clínicos** — VB-MAPP, Denver (confirmados). ABLLS-R (a confirmar).
7. **Guias vencem a cada 4-6 meses** — sistema deve alertar com antecedência.
8. **Hosting no Manus** — infraestrutura atual, com possibilidade de migração futura.
9. **Identidade visual** — cores da Aldeia, logo da árvore, sem nome da clínica nos materiais.

---

## Resumo Executivo

A plataforma Aldeia já possui **22 funcionalidades implementadas** que cobrem dashboards, financeiro básico, comunicação e administração. Para operar como sistema único da clínica sem dependência de ferramentas externas, são necessárias **10 evoluções** em funcionalidades existentes e **14 funcionalidades novas** a serem criadas.

A prioridade máxima é o **Módulo de Gestão de Guias** (Sprint 1), pois impacta diretamente o faturamento e expõe a clínica a riscos legais. Em seguida, a **Evolução Estruturada do Prontuário** (Sprint 2) é fundamental para eliminar retrabalho e permitir relatórios automáticos para convênios.

Com a execução das 10 sprints estimadas, a Aldeia terá um sistema completo, proprietário e diferenciado — superior aos concorrentes de mercado por ser construído sob medida para a realidade operacional da clínica.
