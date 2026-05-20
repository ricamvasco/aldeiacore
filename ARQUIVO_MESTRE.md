# ARQUIVO MESTRE — ALDEIA: Centro de Neurodesenvolvimento e Conexão

**Última Atualização:** 16/05/2026 (atualizado em sessão de 16/05/2026 — Sprints 7-11 concluídas, migração Supabase PostgreSQL completa, 52 testes passando)

> **INSTRUÇÃO PARA O MANUS:** Ao iniciar qualquer tarefa neste projeto, leia este arquivo primeiro. Ele contém o contexto completo da Aldeia. Se precisar de detalhes específicos de uma área, abra o arquivo correspondente no índice (Parte 4).

> **ACESSO AOS ARQUIVOS COMPLETOS:** O ZIP com todos os 459 arquivos organizados (documentos, imagens, PDFs, versões anteriores) está disponível em: https://manus.im/share/file/7e1b3dde-fdc8-4f2c-a406-fba47acd3d17 — Solicite ao usuário que envie o ZIP caso precise acessar os arquivos detalhados.

> **CAMADA 5 — GOOGLE DRIVE (Fonte Primária):** Todos os arquivos da Aldeia estão organizados no Google Drive, na pasta `Aldeia` (ID: `1mVizl4T_bOEpWeHwOvadLS0sktpX4oGa`). Estrutura de subpastas: `01_ESTRATEGICO`, `02_JURIDICO` (ID: `1xH0J6AK...`), `03_FINANCEIRO`, `04_OBRA`, `05_CLINICO`, `06_RH`, `07_MARKETING` (ID: `1NzEmwJ2_tq1O7ijqmA0qHyrb2sXjWBv-`), `08_OPERACIONAL`, `09_IMAGENS`, `10_VERSOES_ANTERIORES`, `Estrategia`, `Jornadas`. O Google Drive é a fonte primária e mais atualizada. Use o CLI `gws` para acessar. Link: https://drive.google.com/drive/folders/1mVizl4T_bOEpWeHwOvadLS0sktpX4oGa

---

## PARTE 1: REGRAS DE OURO E IDENTIDADE

### 1.1. Identidade Corporativa
- **Nome Oficial:** Aldeia — Centro de Neurodesenvolvimento e Conexão (O nome "Clínica Aldeia" foi descontinuado).
- **Slogan:** "Porque nenhuma criança deveria crescer sozinha — é preciso uma aldeia inteira para florescer."
- **Frase de Apoio:** "Conectar é desenvolver. Desenvolver é florescer."
- **Logo:** Árvore estilizada com raízes visíveis (verde + navy). Em redes sociais, usar apenas o símbolo da árvore, sem o nome.
- **Paleta de Cores:** Azul Navy (#0F2A44), Verde Lima (#A6CE39), Verde Escuro (#2E7D32), Off-White (#F7F9FB), Bege Quente (#EDE7DF), Cinza Slate (#5F6B73).
- **Arquivos de Logo:** Ver pasta `IMAGENS/` — arquivos `logo_aldeia_hd.png`, `logo_aldeia_completo.png`, `logo_final_quadrado.png`, `logo_final_horizontal.png`, `icone_final.png`, `aldeia_logo_tree.png`, `aldeia_logo_simbolo.png`.

### 1.2. Dados Fixos
- **CNPJ:** 66.498.867/0001-27
- **Endereço:** Rua Carlos Dietzsch, 150 — Portão, Curitiba/PR.
- **Sócios:** Letícia Mengarda Vasco (Diretora Técnica) e Ricardo Vasco (Rica — Operações/Financeiro).
- **Inauguração Alvo:** 01/07/2026 (cenário realista: agosto/setembro).

### 1.3. Decisões Estratégicas Irreversíveis
1. **Founder-Led Growth:** O marketing é focado nos bastidores da construção e na autoridade da Letícia.
2. **Operação Inicial:** A clínica iniciará operando sem credenciamento formalizado de convênios (foco em particular e reembolso integral).
3. **Remuneração:** Modelo de repasse por sessão (não CLT), estruturado em 7 níveis de carreira (Semente a Árvore, de 24% a 50%).
4. **Financiamento:** A prioridade absoluta para capital de giro é o PRONAMPE 2026 (até R$ 250 mil, Selic + 6%, 72 meses, 12 meses de carência).
5. **Breakeven:** 420 sessões/mês, 70% de ocupação, faturamento bruto de R$ 63 mil, custos fixos de R$ 34 mil. Prazo estimado: 15 meses.

---

## PARTE 2: STATUS ATUAL E PENDÊNCIAS (Maio/2026)

### 2.1. O que está travando a inauguração (Gargalos)
- **Projeto Civil vs RDC-50:** O projeto tem não-conformidades graves. A maioria dos consultórios tem menos de 7,5 m² e o pé-direito está em 2,40m. Reprovará na VISA.
- **Protocolo VISA:** Ainda não foi feito. A análise leva de 30 a 90 dias.
- **Projetos Complementares:** Elétrico e hidráulico ainda não foram contratados.

### 2.2. O que já foi resolvido
- ✅ CNPJ e Contrato Social emitidos (Capital Social: R$ 500.000).
- ✅ Consulta Comercial (SMU) aprovada.
- ✅ Teste do Corante (Sanepar) realizado em 07/05/2026.
- ✅ Estratégia de Instagram (V2) e Calendário Editorial de 30 dias finalizados.
- ✅ Reunião de alinhamento de marketing realizada (14/05/2026) — ver `MKT_24_relatorio_reuniao_14mai.md`.
- ✅ Conta de anúncios Meta Ads criada e vinculada ao perfil da Letícia.
- ✅ Identidade visual e Brand Book da Letícia entregues pela equipe de marketing.
- ✅ Google Drive configurado como Camada 5 de armazenamento (pasta Aldeia).
- ✅ Manuais de RH e Operações redigidos.
- ✅ Plano de carreira 7 níveis definido.
- ✅ Reunião final jurídica realizada (15/05/2026) — estratégias, proposta e cronograma consolidados.
- ✅ Modelo de honorários de reembolso definido com escritório Höschele e Silva.

### 2.3. Plataforma Digital (aldeia-dashboards) — Status Maio/2026
**Checkpoint atual:** v74336c94 | **Tecnologia:** React 19 + tRPC + PostgreSQL (Supabase) + Tailwind 4

**Módulos implementados e funcionando:**
- ✅ Dashboard Executivo (KPIs gerais, gráficos de ocupação)
- ✅ Dashboard por Área (Fono, TO, Psico, Neuro)
- ✅ Dashboard por Terapeuta (sessões, NPS, evolução)
- ✅ Cadastro de Colaboradores (perfil, nível, área, contato)
- ✅ Cadastro de Pacientes (dados, convênio, responsável)
- ✅ Registro de Sessões (com verificação de guia integrada)
- ✅ Gestão de Guias/Convênios (CRUD, alertas 30/15/7 dias, renovação)
- ✅ Dashboard de Glosas (cruzamento guias vencidas × sessões)
- ✅ NPS Público + QR Code + WhatsApp NPS
- ✅ Relatórios PDF (geração automática)
- ✅ Notificações (alertas de guia, sistema)
- ✅ Painel Admin (configurações, usuários)
- ✅ Protocolos de Avaliação (VB-MAPP 0/0.5/1, Denver +/+/-/-, ABLLS-R 0-4, AFLS 0-4 — scoring customizado por protocolo)
- ✅ Plano Terapêutico Individual - PTI (objetivos SMART, revisão trimestral)
- ✅ Relatório de Evolução Automatizado (para convênios) + Exportação CSV com filtro por convênio/período
- ✅ Supervisão Clínica (registro, feedback, plano de ação)
- ✅ Banco de Atividades/Materiais (biblioteca compartilhada)
- ✅ Avaliação de Desempenho 360° (pares, líderes, famílias)
- ✅ Plano de Carreira Visual (Semente→Árvore, 7 níveis)
- ✅ Banco de Horas / Controle de Ponto
- ✅ Gestão de Férias e Licenças
- ✅ Treinamentos e Capacitações
- ✅ Integração WhatsApp (alertas de guia automáticos)
- ✅ **Controle de Atendimentos para Cobrança** (Sprint 6 — Data, Hora, Paciente, Área, Tipo, Convênio, Duração, Valor, Repasse, Status, Prontuário 24h + filtros + exportação CSV/PDF)
- ✅ **Login por Código de Acesso** (senha compartilhada, sem necessidade de conta Manus — código padrão configurável via Settings > Secrets)
- ✅ **Quick Wins UX** (Sprint 7 — Popup PTI na Agenda, pré-preenchimento no Registro Clínico, CTA "Próximo Paciente")
- ✅ **Documentos Pré-preenchidos** (Sprint 7.5 — 6 templates: Contrato, LGPD, Autorização, Declaração, Relatório Evolução, Anamnese + CSS print)
- ✅ **Fluxos Conectados** (Sprint 8 — Agenda→Registro→Prontuário em 1 clique, notificações in-app, Fluxo Admissão 5 etapas, Painel "Meu Dia", alerta prontuário >24h, checklist admissão)
- ✅ **Módulos Novos P2** (Sprint 9 — Onboarding terapeuta 6 passos, Lista de Espera CRUD, Flag "Supervisão Urgente", Flag "Risco de Evasão")
- ✅ **Painel do Supervisor** (Sprint 10 — Dashboard consolidado de equipe, painel de pendências, cards de terapeutas com métricas, ações rápidas)
- ✅ **Financeiro Avançado** (Sprint 11 — Cobrança Particulares, Histórico de Alterações por Guia, Presença em Lote, Relatório Mensal Automatizado)
- ✅ **Módulos Complementares** (Sprint 13 — Ocorrências/Incidentes, Atas de Reunião, PDI vinculado ao plano de carreira, Horas Automáticas por Sessão)
- ✅ **Login Individual com Convites** — Sistema de convites por email, criação de senha, login email+senha, painel de gerenciamento de convites
- ✅ **Permissões por Role (RBAC)** — Sidebar filtrado por cargo (socio/lider/terapeuta), cargoAldeia no auth.me
- ✅ **Sprint 14: Banco Real Confirmado** — Cadastro de Pacientes e Colaboradores já conectados ao Supabase, seed de 10 pacientes + 8 terapeutas
- ✅ **Sprint 14b: Renomear Registro Clínico → Apontamento** — Nomenclatura corrigida em toda a plataforma
- ✅ **P0: Customização de Protocolos** — Scoring flexível por protocolo (VB-MAPP milestone, Denver pass/fail, ABLLS-R/AFLS escala independência)

**Documentos Clínicos de Referência (20/05/2026):**
- Google Drive: [Aldeia/05_CLINICO/Protocolos/](https://drive.google.com/open?id=12NOqYw36oEoom91M4KOWGAQf0P0PM9kZ)
- VB-MAPP: Manual completo (200 páginas) — 5 componentes, 170 marcos, 3 níveis
- AFLS: 6 volumes (Básicas, Social, Independente, Domésticas, Vocacionais, Escolares) — escala 0-4
- Denver: Checklist por faixa etária — scoring +/+/-/-
- Social Skills Solution (SSS): Manual + programa individualizado de paciente
- Exemplos reais: DaviNovaisfev26.pdf, ProgramaSSS-GaelSandes.pdf
- Análise completa: `analise_protocolos_clinicos.md` na mesma pasta

**Decisões de arquitetura (14/05/2026):**
- **Auth temporário:** Manus OAuth + código de acesso (substituiu Supabase Auth que estava causando bug de modo demo). Supabase Auth foi removido do frontend.
- **Migração banco concluída (16/05/2026):** TiDB/MySQL → Supabase PostgreSQL. Schema convertido (31 tabelas), driver atualizado (mysql2 → postgres), testes passando (52/52). Projeto Supabase: `tstrvgsjfwgvivhnpead`. Pendente: migração de dados reais e remoção da dependência mysql2.
- **UX sequencial:** Diagnóstico identificou 8 de 10 fluxos quebrados (80%). Plataforma trata telas como módulos independentes, sem CTAs de "próximo passo". Quick wins priorizados: popup de objetivos na agenda, pré-preenchimento no registro clínico, CTA "próximo paciente".
- **Multi-tenant (futuro):** Análise de viabilidade SaaS concluída. Custo infra R$ 280/mês para até 20 clínicas. Requer: clinicaId em 28 tabelas, auth próprio, Stripe, landing page, painel super admin. Estimativa: 8-9 semanas.

**Sprints concluídas (16/05/2026):**
- ✅ Sprint 7: Quick Wins UX (P0) — Popup PTI, pré-preenchimento, CTA próximo paciente
- ✅ Sprint 7.5: Documentos Pré-preenchidos — 6 templates com auto-fill
- ✅ Sprint 8: Fluxos Conectados (P1) — Admissão, Meu Dia, alertas, checklist
- ✅ Sprint 9: Módulos Novos (P2 alta) — Onboarding, Lista de Espera, flags urgência/evasão
- ✅ Sprint 10: Painel de Supervisão (P2) — Dashboard supervisor, pendências, equipe
- ✅ Sprint 11: Financeiro Avançado (P2+P3) — Particulares, histórico guias, presença lote, relatório mensal
- ✅ Sprint 13: Módulos Complementares (P2+P3) — Ocorrências, Atas, PDI, Horas Automáticas
- ✅ Sprint 14: Banco Real Confirmado + Seed Data (10 pacientes + 8 terapeutas)
- ✅ Sprint 14b: Renomear Registro Clínico → Apontamento
- ✅ P0: Customização de Protocolos de Avaliação (scoring flexível por protocolo)
- ✅ Login Individual com Convites (email+senha, RBAC por cargo)
- ✅ Migração Supabase (Banco): Schema PostgreSQL criado com 31 tabelas, conexão via transaction pooler

**Próximas sprints pendentes:**
- P1: Datas extras no cadastro (1º contato, 1ª avaliação, início atendimento) + Banco de Médicos
- P1: Separar Relatórios Evolutivos dos Apontamentos (aba própria no prontuário)
- P1: Módulo de Documentos com tags obrigatórias (RG, Laudo, Encaminhamento)
- P1: Diferenciar PTI vs PEI (PTI = trimestral/área, PEI = anual/global)
- P2: Adicionar protocolo SSS (Social Skills Solution)
- P2: Vincular resultados de protocolo → Metas PTI/PEI automaticamente
- P2: AFLS separado em 6 subprotocolos (Básicas, Social, Independente, Domésticas, Vocacionais, Escolares)
- P2: VB-MAPP componentes Barreiras (24 itens) e Transição (18 áreas)
- Portal Família: Acesso externo para pais/responsáveis (evolução, agenda, documentos, comunicação)
- Agenda Inteligente: Otimização de horários, conflitos, encaixes
- IA: Inteligência Artificial (predição de evasão, sugestões)
- Migração Auth: Substituir Manus OAuth por auth próprio (futuro)
- Deploy independente: Sair do Manus hosting (futuro)

---

## PARTE 3: CONTEÚDO ESSENCIAL POR ÁREA (Condensado)

### 3.1. OBRA E REGULARIZAÇÃO
**Fluxo Obrigatório (ordem estrita de dependências):**
1. Consulta Comercial (SMU) → ✅ Aprovada
2. Adequação RDC-50 → ❌ Pendente (consultórios abaixo de 7,5 m², pé-direito 2,40m, faltam pias)
3. Protocolo VISA (SMS) → ❌ Pendente (30-90 dias de análise)
4. Alvará de Reforma (SMU) → ❌ Pendente
5. Obra Física → Deve seguir exatamente o projeto aprovado
6. CVCO (Habite-se) → Pós-obra
7. CLCB (Bombeiros) → Pós-obra
8. Alvará de Funcionamento → Exige CVCO + CLCB
9. Licença Sanitária → Vistoria final da VISA na clínica pronta

**Não-conformidades do projeto civil (RDC-50):**
Neuropsicólogo (7,34m²), Psico.1 (6,12m²), Psico.2 (5,83m²), Fono.1 (5,88m²), Fono.2 (~5m²), Fono.3 (4,51m²), Fono.4 (5,84m²), Fono.5 (7,02m²), T.O.1 (~7m²), T.O.2 (~6m²), T.O.3 (7,04m²), T.O.4 (5,84m²) — todos abaixo do mínimo de 7,50m².

### 3.2. JURÍDICO E REGULATÓRIO
**Contrato Letícia (Cerne):** Cláusula de non-compete (R$ 100 mil, 6 meses) é nula por falta de compensação financeira. Defesa: "escudo trabalhista" — pejotização comprova vínculo empregatício (subordinação, pessoalidade, habitualidade). Se a Cerne ameaçar, Letícia ameaça com Reclamatória Trabalhista.

**Estratégia de Convênios sem Credenciamento:**
1. Reembolso Integral por Falha na Rede (RN 259/2011 ANS — 10 dias úteis)
2. Manutenção do Vínculo Terapêutico (liminares para TEA)
3. Pressão Regulatória: NIPs na ANS → Notificação Extrajudicial → Denúncia ANS

**VOAM:** Credenciamento fechado, mas Aldeia está no radar. Plano: dossiê profissional + criação de demanda (NIPs) + reembolso integral + notificação extrajudicial.

**Decisões da Reunião Jurídica (15/05/2026) — Escritório Höschele e Silva:**
- **Honorários de Reembolso:** Reembolso integral → escritório cobra R$ 2.200–3.000 fixo por ação, saldo vai para a Aldeia. Reembolso parcial (tabela do plano) → divisão 50/50. Dano moral → 30% escritório, 70% pais (incentivo para os pais entrarem no processo).
- **Fórum Preferido: Vara Cível** (não Juizado Especial) — permite liminar em 3–5 dias. Estratégia: múltiplos processos distribuídos por dependência (um por mês de atendimento), com pedido em dois níveis (Split the Baby: integral como principal, tabela do plano como subsidiário).
- **Caso-piloto no Juizado:** Testar com um processo difícil para sentir a receptividade do juiz local.
- **Cartilha para os Pais:** Escritório elaborará cartilha de reembolso administrativo por plano. Após negativa, pai envia notificação extrajudicial (sem identificação do escritório) dando 48h antes de judicializar.
- **Hipossuficiência:** Pais que comprovarem incapacidade financeira entram na Vara Cível sem custas. Liminar em 3 dias se documentação estiver em ordem.
- **Proposta em Pacote Único:** Confirmado verbalmente — escritório fechará todos os contratos em pacote único, eliminando a divisão confusa entre honorários e custos operacionais.
- **Parceria Estratégica (em negociação):** Rica propôs trocar honorários de êxito do credenciamento pelos ganhos do escritório com reembolsos dos pais. Advogado sinalizou interesse, mas precisa consultar sócio Jefferson. Contrapartida do escritório: participação minoritária na Aldeia ou retainer mensal fixo pós-credenciamento. **Pauta da próxima reunião.**
- **Projeção:** 90 pacientes/ano 1 → 45 com plano → R$ 180.000/mês em pedidos de reembolso → R$ 300.000/mês em volume processual. Breakeven com 28 pacientes particulares.

### 3.3. FINANCEIRO
**PRONAMPE 2026:** Selic + até 6% a.a., até 72 meses, carência de 12 meses, aval pessoal. Limite: 50% do Capital Social = R$ 250 mil (teto). Processo: e-CAC → autorizar compartilhamento → banco PJ → simulação → assinatura digital.

**Capital de Giro Necessário:** R$ 150-200 mil para cobrir os primeiros 12-15 meses até o breakeven.

### 3.4. MARKETING (Founder-Led Growth)
**Posicionamento:** "Oceano Azul de Cuidado Sistêmico" — a jornada real da Letícia e Rica construindo a clínica dos sonhos.

**Pilares:** (1) Jornada do Fundador, (2) Educação e Acolhimento, (3) Diferencial Sistêmico, (4) Autoridade Técnica.

**Stories diários:** Manhã (rosto + enquete), Tarde (bastidores + ciência), Noite (caixinhas + CTA).

**Personas:** Mãe Diagnóstico Recente (acolhimento), Mãe Upgrade (diferenciais técnicos), Profissional B2B (conhecimento avançado).

**Status Atual (Maio/2026):**
- Equipe contratada: Camila (estrategista) — Investimento: R$ 3.000/mês.
- Perfil @leticiavasco.psi: 890 seguidores, taxa de engajamento > 3%.
- Formato prioritário: Reels (virada de carrossel para vídeo).
- Mídia paga: R$ 300/mês (R$ 200 alcance + R$ 100 engajamento). Pagamento pré-pago.
- Roadmap: Maio (aprendizado) → Junho (+1.000 seguidores) → Julho (gerar leads/conversas).
- Framework de referência: Leandro Ladeira — 7 Tipos de Interação (ver `MKT_25_framework_ladeira_7interacoes.md`).
- Gap principal: engajamento vem da própria audiência; necessário furar a bolha com mídia paga e collabs.

### 3.5. RH E CORPO CLÍNICO
**7 Níveis de Carreira (repasse por sessão):**
Semente (Estagiário): Bolsa fixa | Broto (AT): 24-27% | Caule (Júnior): 28-31% | Ramo (Pleno): 32-35% | Folha (Sênior): 36-39% | Fruto (Especialista): 40-45% | Árvore (Diretor): 45-50%

**Promoção exige 4 pilares simultâneos:** Tempo de casa + Certificações + KPIs clínicos + EBITDA positivo da clínica.

### 3.6. OPERAÇÕES
**4 Frentes Administrativas (sem Supervisão Clínica):**
1. Recepção: Acolhe, tria (particular vs convênio), aplica questionário.
2. Agendamento: Cruza demanda com Matriz de Especialidades dos terapeutas.
3. Convênios: Nenhuma sessão sem autorização prévia. Auditoria de pedido médico antes de enviar à operadora.
4. Faturamento: NFs, lote XML (TISS), tratamento de glosas.

### 3.7. BRANDING
**Identidade Visual:** Árvore sem nome em redes sociais. Paleta navy + verde lima. Materiais "sensory-friendly" (texturas, acabamentos táteis). Uniformes com nome + nível do terapeuta.

### 3.8. ESTRATÉGIA GERAL
**Plano Mestre 60 Dias:** Dividido em sprints semanais cobrindo todas as frentes simultaneamente. Prioridade: regularização → financeiro → equipe → marketing → inauguração.

### 3.9. CLÍNICO — ESPECIALIDADES E PROTOCOLOS
**Especialidades Clínicas Definitivas (7):** Neuropsicologia, Pedagogia, Psicologia, Fonoaudiologia, Terapia Ocupacional, Psicomotricidade, Integração Sensorial.

**Atividades Complementares (vetores de desenvolvimento — não são especialidades formais):** Jiu-jitsu (→ Psicomotricidade, TO, Psico), Judô (→ Psicomotricidade, TO, Psico), Botânica (→ Pedagogia, Neuropsico), Circo (→ Psicomotricidade, IS, TO).

**Nota de arquitetura:** Musicoterapia foi removida da lista de especialidades. A tabela `areas` no banco precisa ser atualizada (ver `OPS_22_task_arquitetura_especialidades.md`).

**Protocolos ABA mapeados (base CERNE):** Checklist ESDM, TTT, PEAK, EFL, VBMAPP, AFLS, SSS, PFA & SBT — ver `CLIN_01_especialidades_e_protocolos.md`.

**Status:** Protocolos das 7 especialidades clínicas ainda a mapear — aguardando materiais da Letícia.

### 3.10. MÉTODO ALDEIA 360 (Em Construção)
**Conceito:** Sistema integrado de governança clínica que conecta todas as especialidades em torno de metas compartilhadas por paciente. Principal diferencial competitivo da Aldeia e ativo a ser patenteado.

**Problema que resolve:** No mercado atual, cada especialidade trabalha isoladamente. Não existe construção conjunta de metas, comunicação entre profissionais, ou monitoramento de impactos cruzados entre disciplinas.

**Componentes do Método:**
1. Metas 360 por paciente (construídas em conjunto por todas as especialidades envolvidas)
2. Governança de colaboração (ritos, frequência, responsáveis — em design)
3. Protocolos integrados por especialidade (em mapeamento)
4. Visualizações de dados superiores ao padrão do mercado (em design)
5. Infraestrutura na plataforma aldeia-dashboards (pendente — depende dos itens acima)

**Status:** Em desenvolvimento ativo. Aguardando materiais clínicos de todas as especialidades.

---

## PARTE 4: ÍNDICE DE ARQUIVOS (Nomenclatura Padronizada)

### OBRA (9 arquivos)
| Arquivo | Conteúdo |
|---|---|
| `OBRA_02_analise_projeto_rdc50.md` | Relatório de não-conformidades do projeto civil vs ANVISA |
| `OBRA_05_fluxo_pos_sanepar.md` | Próximos passos após teste do corante |
| `OBRA_08_notas_projeto_civil.md` | Anotações sobre o projeto civil |
| `OBRA_09_pesquisa_aprovacao_projeto.md` | Pesquisa sobre processo de aprovação em Curitiba |
| `OBRA_10_checklist_documentos_alvaras.md` | Lista de documentos para cada alvará |
| `OBRA_11_reforma_minima_alvaras.md` | Reforma mínima + alvarás de funcionamento |
| `OBRA_12_requisitos_regulatorios.md` | Requisitos regulatórios completos |
| `OBRA_13_deep_dive_obra_estrutura.md` | Detalhamento completo da obra e estrutura |
| `OBRA_14_guia_abertura_clinica.md` | Guia de abertura da clínica |
| `OBRA_15_guia_abertura_roadmap.md` | Roadmap de abertura |
| `OBRA_16_analise_reforma_minima_financeira.md` | Análise reforma mínima vs financeira |
| `OBRA_17_orcamento_detalhado_reforma.md` | Orçamento detalhado da reforma |

### JURÍDICO (6 arquivos)
| Arquivo | Conteúdo |
|---|---|
| `JUR_01_estrategia_juridica.md` | Estratégia jurídica e regulatória completa |
| `JUR_02_analise_contrato_cerne.md` | Análise cláusula a cláusula do contrato PJ da Letícia |
| `JUR_03_plano_credenciamento_voam.md` | Plano de 5 frentes para forçar credenciamento VOAM |
| `JUR_04_guia_antecipacao_convenios.md` | Guia para antecipar credenciamento em operadoras |
| `JUR_05_cronograma_ataque_regulatorio.md` | Timeline das ações regulatórias |
| `JUR_06_acoes_juridicas_complementares.md` | Ações jurídicas adicionais |
| `JUR_07_analise_codigo_etica_cfp.md` | Análise do Código de Ética do CFP |
| `JUR_08_analise_proposta_juridica.md` | Avaliação de proposta de escritório |
| `JUR_09_cronograma_juridico.md` | Timeline de ações jurídicas |
| `JUR_10_dados_juridicos.md` | Dados e informações jurídicas compiladas |
| `JUR_11_guia_reuniao_juridica.md` | Pauta e roteiro para reunião com advogado |
| `JUR_12_pesquisa_juridica.md` | Pesquisa de jurisprudência |
| `JUR_13_resumo_juridico_pendente.md` | Pendências jurídicas abertas |
| `JUR_14_detalhamento_juridico_regulatorio.md` | Detalhamento completo da frente jurídica |
| `JUR_15_responsabilidades_escritorio.md` | Responsabilidades do escritório de advocacia |
| `JUR_16_risco_regulacao_analise.md` | Análise completa de risco regulatório |
| `JUR_17_carta_apresentacao_operadoras.md` | Carta de apresentação para operadoras |

### FINANCEIRO (17 arquivos)
| Arquivo | Conteúdo |
|---|---|
| `FIN_01_guia_pronampe.md` | Guia completo PRONAMPE 2026 |
| `FIN_02_calculo_capital_giro.md` | Cálculo detalhado da necessidade de capital |
| `FIN_03_detalhamento_financeiro.md` | Detalhamento da frente financeira |
| `FIN_04_guia_negociacao_bancaria.md` | Roteiro para negociar com gerente do banco |
| `FIN_05_alternativas_financiamento.md` | Outras opções além do PRONAMPE |
| `FIN_06_pesquisa_alternativas_credito.md` | Pesquisa de linhas de crédito |
| `FIN_07_custos_essencial_vs_desejavel.md` | Custos essenciais vs desejáveis |
| `FIN_08_dossie_financeiro_consolidado.md` | Dossiê financeiro consolidado |
| `FIN_09_cash_flow_hipotetico.md` | Cash flow hipotético (cenário maturidade) |
| `FIN_10_cash_flow_referencia.md` | Cash flow de referência |
| `FIN_11_dre_hipotetico.md` | DRE hipotético |
| `FIN_12_dre_referencia.md` | DRE de referência |
| `FIN_13_fluxo_caixa_detalhado.md` | Fluxo de caixa detalhado (Mês 1-12) |
| `FIN_14_fluxo_caixa_contingencia.md` | Fluxo de caixa de contingência e burn rate |
| `FIN_15_analise_comparativa_financeira.md` | Análise comparativa Aldeia vs mercado |
| `FIN_16_parecer_cfo_auditoria.md` | Parecer do CFO: auditoria DRE + Cash Flow |
| `FIN_17_prazos_pagamento_convenios.md` | Prazos de pagamento de planos de saúde |
| `FIN_18_valores_repasse_unimed.md` | Valores de repasse Unimed |
| `FIN_19_benchmark_precos_repasses.md` | Benchmark de preços e repasses em Curitiba |
| `FIN_20_projecao_atendimentos_faturamento.md` | Projeção de atendimentos e faturamento |
| `FIN_21_verificacao_custos.md` | Verificação completa de custos |
| `FIN_22_custos_rh_bpo.md` | Custos de RH e BPO financeiro |
| `FIN_23_custos_seguranca.md` | Custos de serviço de segurança |
| `FIN_24_validacao_demanda.md` | Validação de demanda com evidências reais |

### MARKETING (21 arquivos)
| Arquivo | Conteúdo |
|---|---|
| `MKT_01_estrategia_instagram.md` | Estratégia completa de Instagram (Founder-Led Growth) |
| `MKT_02_calendario_editorial_completo.md` | Calendário editorial de 30 dias |
| `MKT_03_calendario_semana_1.md` | Detalhamento semana 1 |
| `MKT_04_calendario_semana_2.md` | Detalhamento semana 2 |
| `MKT_05_calendario_semana_3.md` | Detalhamento semana 3 |
| `MKT_06_calendario_semana_4.md` | Detalhamento semana 4 |
| `MKT_07_calendario_macro_3meses.md` | Planejamento macro de 3 meses |
| `MKT_08_calendario_micro_sem1_2.md` | Micro-calendário semanas 1-2 |
| `MKT_09_calendario_micro_sem3_4.md` | Micro-calendário semanas 3-4 |
| `MKT_10_plano_acao_instagram.md` | Plano de ação para implementação |
| `MKT_11_deep_dive_marketing.md` | Deep dive em marketing |
| `MKT_12_segmentacao_anuncios.md` | Segmentação de público para tráfego pago |
| `MKT_13_plano_captacao_local.md` | Plano de captação de pacientes na região |
| `MKT_14_instagram_check.md` | Checklist de otimização do perfil |
| `MKT_15_pesquisa_carrosseis_reels.md` | Pesquisa de tendências de carrosséis e reels |
| `MKT_16_pesquisa_founder_led_growth.md` | Pesquisa sobre Founder-Led Growth |
| `MKT_17_pesquisa_instagram_2026.md` | Pesquisa de algoritmo Instagram 2026 |
| `MKT_18_pesquisa_stories_2026.md` | Pesquisa de melhores práticas de stories |
| `MKT_19_plano_founder_led_growth.md` | Plano de ação Founder-Led Growth (Letícia) |
| `MKT_20_conteudo_educativo_tea.md` | Conteúdo educativo TEA: roteiros carrosséis/reels |
| `MKT_21_estrategia_marketing_conteudo.md` | Estratégia de marketing de conteúdo |
| `MKT_22_editorial_calendar_skill.md` | Guia de calendário editorial (skill) |
| `MKT_23_marketing_strategy_skill.md` | Guia de estratégia de marketing (skill) |
| `MKT_24_relatorio_reuniao_14mai.md` | Relatório da reunião de marketing 14/05/2026 |
| `MKT_25_framework_ladeira_7interacoes.md` | Framework Ladeira: 7 tipos de interação |
| `MKT_26_playbook_jogadas_crescimento.md` | Playbook de Jogadas (Growth & Retention) |

### RH (16 arquivos)
| Arquivo | Conteúdo |
|---|---|
| `RH_01_plano_carreira_7niveis.md` | Plano de carreira completo (Semente a Árvore) |
| `RH_02_manual_trajetoria_corpo_tecnico.md` | Manual da Trajetória Aldeia (cultura, rituais, valores) |
| `RH_03_job_descriptions_niveis.md` | Descrição de cargos por nível |
| `RH_05_formulario_avaliacao_desempenho.md` | Formulário de avaliação de desempenho |
| `RH_06_lista_talentos_hunting.md` | Lista de profissionais mapeados |
| `RH_07_deep_dive_rh.md` | Deep dive em RH |
| `RH_08_plano_cargos_salarios_final.md` | Plano de cargos e salários (final corrigido) |
| `RH_09_plano_cargos_benchmark.md` | Plano de cargos com benchmark |
| `RH_10_recrutamento_mentorias.md` | Recrutamento + mentorias como pipeline |
| `RH_11_status_recrutamento.md` | Status de recrutamento |
| `RH_12_perfil_profissionais.md` | Perfil de profissionais |
| `RH_13_plano_cargos_original.md` | Plano de cargos (versão original) |
| `RH_14_plano_cargos_opcao1.md` | Plano de cargos (opção 1) |
| `RH_15_plano_cargos_final_revisado.md` | Plano de cargos (final revisado) |
| `RH_16_plano_cargos_corpo_clinico.md` | Plano de cargos (corpo clínico) |

### OPERAÇÕES (21 arquivos)
| Arquivo | Conteúdo |
|---|---|
| `OPS_01_manual_4frentes_administrativas.md` | Manual das 4 frentes administrativas |
| `OPS_02_guia_monitoramento_kpis.md` | Guia de KPIs da clínica e dos profissionais |
| `OPS_03_checklist_inauguracao.md` | Checklist master de inauguração |
| `OPS_04_cronograma_administrativo.md` | Cronograma administrativo |
| `OPS_05_manual_operacional_deep_dive.md` | Manual operacional aprofundado |
| `OPS_06_deep_dive_operacoes.md` | Deep dive em operações |
| `OPS_07_deep_dive_protocolos_clinicos.md` | Protocolos clínicos detalhados |
| `OPS_08_deep_dive_tecnologia_digital.md` | Tecnologia e sistemas digitais |
| `OPS_09_deep_dive_terceiros_facilities.md` | Terceiros e facilities |
| `OPS_10_guia_avaliacao_sistemas.md` | Guia para avaliar softwares de gestão |
| `OPS_11_kpis_clinica.md` | KPIs específicos da clínica |
| `OPS_12_kpis_profissionais.md` | KPIs por nível profissional |
| `OPS_13_plano_operacional_semanal.md` | Plano operacional semanal |
| `OPS_14_qualidade_atendimento.md` | Qualidade de atendimento: lacunas e soluções |
| `OPS_15_retool_queries_dashboards.md` | Queries SQL e guia de dashboards |
| `OPS_16_supabase_schema.md` | Schema do banco de dados |
| `OPS_17_referencias_clinicas.md` | Referências clínicas |
| `OPS_18_checklist_implantacao.md` | Checklist de implantação |
| `OPS_19_culture_manual.md` | Manual de cultura organizacional |
| `OPS_20_kpis_clinica_v2.md` | KPIs clínica (versão 2) |
| `OPS_21_kpis_profissionais_v2.md` | KPIs profissionais (versão 2) |

### BRANDING (9 arquivos)
| Arquivo | Conteúdo |
|---|---|
| `BRAND_01_identidade_oficial.md` | Nome, logo, paleta, regras de uso |
| `BRAND_02_ideias_adesivos.md` | Ideias de adesivos para a clínica |
| `BRAND_03_deep_dive_enxoval_branding.md` | Deep dive em branding e enxoval |
| `BRAND_04_mapeamento_local.md` | Mapeamento do entorno e vizinhança |
| `BRAND_05_conceito_visual.md` | Conceito visual da marca |
| `BRAND_06_diretrizes_visuais.md` | Diretrizes visuais de referência |
| `BRAND_07_notas_visuais.md` | Notas visuais |
| `BRAND_08_logo_notes.md` | Notas sobre a logo |
| `BRAND_09_brand_identity_skill.md` | Guia de identidade de marca |

### ESTRATÉGIA (21 arquivos)
| Arquivo | Conteúdo |
|---|---|
| `ESTR_01_plano_mestre_60_dias.md` | Plano mestre de 60 dias |
| `ESTR_02_proximos_passos_60_dias.md` | Próximos passos detalhados |
| `ESTR_03_roteiro_encontro_fundadores.md` | Roteiro para encontro entre Rica e Letícia |
| `ESTR_04_deep_dive_rituais_pre_inauguracao.md` | Rituais de pré-inauguração |
| `ESTR_05_roteiro_apresentacao_encantamento.md` | Roteiro de apresentação de encantamento |
| `ESTR_06_planejamento_estrategico_detalhado.md` | Planejamento estratégico detalhado |
| `ESTR_07_plano_acao_integrado.md` | Plano de ação integrado |
| `ESTR_08_visao_geral_aldeia.md` | Visão geral da Aldeia |
| `ESTR_09_plano_evolucao_plataforma.md` | Plano de evolução da plataforma digital |
| `ESTR_10_mapeamento_plataforma.md` | Mapeamento da plataforma |
| `ESTR_11_pitch_deck_v2.md` | Pitch deck (versão 2) |
| `ESTR_12_pitch_deck_revisao_13.md` | Pitch deck (revisão 13) |
| `ESTR_13_pitch_deck_revisao_10.md` | Pitch deck (revisão 10) |
| `ESTR_14_pitch_deck_revisao_7_8.md` | Pitch deck (revisão 7/8) |
| `ESTR_15_conteudo_slides_planejamento.md` | Conteúdo de slides de planejamento |
| `ESTR_16_detalhamento_marketing_60dias.md` | Detalhamento marketing 60 dias |
| `ESTR_17_detalhamento_rh_60dias.md` | Detalhamento RH 60 dias |
| `ESTR_18_plano_acao_financeiro_60dias.md` | Plano de ação financeiro 60 dias |
| `ESTR_19_plano_acao_operacoes_60dias.md` | Plano de ação operações 60 dias |
| `ESTR_20_pitch_deck_skill.md` | Guia de pitch deck |

### IMAGENS (55 arquivos)
Logos, uniformes, banners, dashboards e materiais visuais. Destaques:
- `logo_aldeia_hd.png` — Logo principal em alta resolução
- `logo_aldeia_completo.png` — Logo completa
- `logo_final_quadrado.png` — Versão quadrada (redes sociais)
- `logo_final_horizontal.png` — Versão horizontal
- `icone_final.png` — Ícone/símbolo da árvore
- `aldeia_logo_tree.png` — Árvore isolada
- `aldeia_logo_simbolo.png` — Símbolo isolado
- `uniforme_01_verde_frente.png` a `uniforme_04_cinza_costas.png` — 8 variações de uniformes
- `banner_aldeia_opcao1/2/3.png` — Propostas de banner
- `aplicacao_rede_social.png` — Aplicação em redes sociais
- `aplicacao_papelaria.png` — Aplicação em papelaria

### UPLOADS / PDFs (17 arquivos)
- `19.EstudoPreliminar_ClinicaAldeia_Ricardo_R00.pdf` — Estudo preliminar do projeto
- `Clinica_DetalhamentoCilvil_R01.pdf` — Detalhamento civil
- `CNPJALDEIA.pdf` — Cartão CNPJ
- `CONTRATOSOCIALASSINADO-ALDEIA.pdf` — Contrato social
- `COMPARATIVODEORÇAMENTOS.pdf` — Comparativo de orçamentos
- `Cronograma_Acoes_Imediatas_Aldeia.pdf` — Cronograma de ações imediatas
- `Planejamento_Estratégico_2025-2027_Aldeia.pdf` — Planejamento estratégico
- `propostaaldeiaHöscheleeSilvaAdvogadosAssociados.pdf` — Proposta jurídica
- `cfp_codigo_etica.pdf` — Código de ética CFP
- E mais 8 PDFs complementares

---

*Total: 119 arquivos .md organizados + 55 imagens + 17 PDFs = 191 arquivos.*
*Localização: `/home/ubuntu/aldeia-organizado/`*

---

## PARTE 5: GOOGLE DRIVE — CAMADA DE DOCUMENTOS PRIMÁRIOS

O Google Drive da Aldeia é a **fonte primária e mais atualizada** de todos os documentos. O GitHub contém os arquivos .md processados e indexados; o Drive contém os originais, PDFs, áudios e versões de trabalho.

**Acesso via CLI:** `gws drive files list` (autenticado como conta Google da Aldeia)

| Pasta no Drive | Conteúdo | ID da Pasta |
|:---|:---|:---|
| **Aldeia** (raiz) | Pasta principal com todas as subpastas | `1mVizl4T...` |
| **02_JURIDICO** | 17 arquivos jurídicos completos (JUR_01 a JUR_17) | `1xH0J6AK...` |

**Arquivos-chave no Drive (Jurídico):**
- `JUR_08_analise_proposta_juridica.md` — Proposta completa do escritório Höschele e Silva com análise crítica
- `JUR_09_cronograma_juridico.md` — Cronograma de ações com divisão Rica / Letícia / Escritório
- `JUR_15_responsabilidades_escritorio.md` — Escopo completo do escritório (10 blocos, R$ 35.500–53.500/ano)
- `propostaaldeiaHöscheleeSilvaAdvogadosAssociados.pdf` — Proposta original em PDF

**Documentos gerados na sessão de 15/05/2026:**
- `REUNIAO_FINAL_JURIDICA_ALDEIA.md` — Consolidado completo para a reunião final (estratégias + proposta + cronograma)
- `TRANSCRICAO_E_ATUALIZACOES_JURIDICA.md` — Transcrição da reunião + 8 atualizações necessárias identificadas

---

## PARTE 6: JORNADAS, ANÁLISES E DIAGNÓSTICOS (Google Drive)

**Pasta:** `Aldeia/Jornadas/` e `Aldeia/Estrategia/` no Google Drive

| Documento | Conteúdo | Localização |
|:---|:---|:---|
| `01-jornada-paciente-detalhada.md` | Jornada ideal do paciente/família — 10 fases, nível operacional (estacionamento, recepção, senhas, salas, feedback). Inclui tabela de itens físicos + digitais necessários. | [Drive](https://drive.google.com/open?id=1rh-pXSE1QV-5ra_OVXPv7FZvwB5tzTsw) |
| `02-jornada-terapeuta-detalhada.md` | Jornada ideal do terapeuta — rotina hora a hora, cada touchpoint com a plataforma, frequência de uso por aba, 13 pontos de melhoria UX/UI priorizados. | [Drive](https://drive.google.com/open?id=1idiikFzYR8Ew2vmOXAVofKtgRp1tZxav) |
| `03-analise-saas-multitenant.md` | Análise de viabilidade SaaS multi-tenant — custos de infra, escopo técnico, modelo de preço, roadmap de 8-9 semanas. | [Drive](https://drive.google.com/open?id=16hioVsIvlbTFG6rlVurboDMWh32wu4rX) |
| `04-diagnostico-ux-jornada.md` | Diagnóstico UX vs Jornada — mapeamento de 10 fluxos sequenciais, 8 quebrados (80%), quick wins P0/P1/P2 priorizados. | [Drive](https://drive.google.com/open?id=19HRMV0YaiGaZZfGtSc6zC7weDGJOYxNh) |
| `05-jornada-supervisor-detalhada.md` | Jornada ideal do supervisor de área — rotina semanal, supervisão individual/grupal, revisão de PTIs, reunião de equipe, gestão de crises. 8 pontos de melhoria UX/UI. Itens físicos: R$ 15.510. | [Drive](https://drive.google.com/open?id=1P-gWgTahN2BlGLm0l8JdhrarF9ta0hbU) |
| `06-jornada-administrativo-detalhada.md` | Jornada ideal do administrativo/recepção (Nyccole) — rotina diária completa, fluxo de novo paciente, gestão de guias, faturamento, agenda, comunicação. 10 pontos de melhoria UX/UI. Itens físicos: R$ 29.030. | [Drive](https://drive.google.com/open?id=1DnmhA6kDzjC1D-XUYIj1-hFRSBCnvYn-) |
| `diagrama-paciente-detalhado.png` | Diagrama visual da jornada do paciente (Mermaid) | Drive: Aldeia/Jornadas/ |
| `diagrama-terapeuta-detalhado.png` | Diagrama visual da jornada do terapeuta (Mermaid) | Drive: Aldeia/Jornadas/ |

**Status:** Todas as 4 jornadas concluídas (Paciente, Terapeuta, Supervisor, Administrativo). Total de 31 pontos de melhoria UX/UI identificados.
