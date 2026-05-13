# Mapeamento Completo — Plataforma Aldeia

> Documento consolidado com tudo que foi implementado, o que está pendente, e o roadmap completo baseado nos vídeos da Letícia, nas plataformas discutidas e nas necessidades operacionais da clínica.

---

## 1. O QUE JÁ ESTÁ IMPLEMENTADO (31 módulos)

### Visão Geral & Dashboards
| Módulo | Status | Descrição |
|--------|--------|-----------|
| Dashboard Executivo | ✅ Pronto | Visão para sócios (Rica e Letícia) — KPIs financeiros, ocupação, NPS |
| Dashboard por Área | ✅ Pronto | Visão para líderes — métricas por especialidade |
| Dashboard Terapeuta | ✅ Pronto | Visão individual — KPIs pessoais e jornada de carreira |
| Dashboard de Glosas | ✅ Pronto | Cruzamento guias vencidas × sessões sem guia válida |

### Financeiro
| Módulo | Status | Descrição |
|--------|--------|-----------|
| Dashboard Financeiro | ✅ Pronto | Receita, despesas, lucro, fluxo de caixa |
| Contas a Receber | ✅ Pronto | Pagamentos por paciente, inadimplência |
| Comissionamento | ✅ Pronto | Repasse por terapeuta com bônus NPS/prontuário |
| Simulador de Ganhos | ✅ Pronto | 7 níveis (Semente→Árvore), projeção por sessões |
| Metas Editáveis | ✅ Pronto | Metas configuráveis por área/terapeuta |
| Produtividade | ✅ Pronto | Desempenho por terapeuta |

### Clínico
| Módulo | Status | Descrição |
|--------|--------|-----------|
| Registro de Sessões | ✅ Pronto | CRUD com calendário interativo |
| Gestão de Guias | ✅ Pronto | CRUD, alertas 30/15/7 dias, checklist renovação |
| Prontuário Digital | ✅ Pronto | Templates por área, vinculado ao Portal Família |
| Gestão de Salas | ✅ Pronto | Mapa visual com ocupação em tempo real |
| Agenda Visual | ✅ Pronto | Calendário interativo de agendamentos |

### Pessoas
| Módulo | Status | Descrição |
|--------|--------|-----------|
| Cadastro de Colaboradores | ✅ Pronto | CRUD de terapeutas com níveis e áreas |
| Cadastro de Pacientes | ✅ Pronto | CRUD conectado ao banco real |
| Onboarding | ✅ Pronto | Painel de onboarding para novos terapeutas |
| Portal Família | ✅ Pronto | Área pública para famílias acompanharem evolução |

### Comunicação & NPS
| Módulo | Status | Descrição |
|--------|--------|-----------|
| NPS Público | ✅ Pronto | Formulário público de avaliação |
| QR Code NPS | ✅ Pronto | Gerador com presets e modelos salvos |
| WhatsApp NPS | ✅ Pronto | Envio automático pós-sessão |
| WhatsApp Métricas | ✅ Pronto | Dashboard de envios e respostas |
| Alertas WhatsApp Guias | ✅ Pronto | Envio automático 30/15/7 dias para famílias |
| Notificações | ✅ Pronto | Push notifications para sócios |

### Administrativo
| Módulo | Status | Descrição |
|--------|--------|-----------|
| Painel Admin | ✅ Pronto | Configurações gerais |
| Exportar Calendário | ✅ Pronto | Feed iCal em tempo real |
| Relatórios PDF | ✅ Pronto | Geração com stepper visual |

---

## 2. O QUE FALTA IMPLEMENTAR — BASEADO NOS VÍDEOS DA LETÍCIA

### Sprint 2: Gestão de Pessoas & Plano de Carreira (PRIORIDADE ALTA)

A Letícia enfatizou fortemente a necessidade de um **plano de carreira estruturado** e **avaliação de desempenho** para reter terapeutas.

| Item | Prioridade | Descrição |
|------|-----------|-----------|
| Avaliação de Desempenho 360° | 🔴 Alta | Avaliação por pares, líderes e famílias. Ciclo trimestral. Critérios: pontualidade, prontuário em dia, NPS, evolução dos pacientes, participação em supervisão |
| Plano de Carreira Visual | 🔴 Alta | Visualização da jornada Semente→Árvore com critérios claros para promoção. Cada nível com requisitos mensuráveis (tempo, NPS, sessões, capacitações) |
| Banco de Horas / Controle de Ponto | 🟡 Média | Registro de entrada/saída, horas extras, banco de horas. Integração com folha de pagamento |
| Gestão de Férias e Licenças | 🟡 Média | Calendário de férias com impacto na agenda. Substituição automática de terapeuta |
| Treinamentos e Capacitações | 🟡 Média | Registro de cursos, certificações, horas de supervisão. Requisito para promoção de nível |

### Sprint 3: Inteligência Clínica & Protocolos (PRIORIDADE ALTA)

A Letícia mencionou a importância de **protocolos padronizados** e **acompanhamento de marcos do desenvolvimento**.

| Item | Prioridade | Descrição |
|------|-----------|-----------|
| Protocolos de Avaliação (VB-MAPP, Denver, ABLS, AFLS) | 🔴 Alta | Aplicação digital dos protocolos com scoring automático. Gráfico de evolução por domínio |
| Plano Terapêutico Individual (PTI) | 🔴 Alta | Objetivos por área, metas SMART, revisão trimestral. Vinculado ao prontuário e visível no Portal Família |
| Relatório de Evolução Automatizado | 🔴 Alta | Geração automática de relatório para convênios baseado nos dados do prontuário + protocolos |
| Supervisão Clínica | 🟡 Média | Registro de supervisões, feedback do supervisor, plano de ação. Obrigatório para promoção |
| Banco de Atividades/Materiais | 🟡 Média | Biblioteca compartilhada de atividades por área e objetivo. Terapeutas podem contribuir e avaliar |

### Sprint 4: Experiência da Família (PRIORIDADE ALTA)

A Letícia destacou que **famílias engajadas** = melhores resultados clínicos e menor churn.

| Item | Prioridade | Descrição |
|------|-----------|-----------|
| Portal Família 2.0 — Chat com Terapeuta | 🔴 Alta | Comunicação assíncrona entre família e equipe. Histórico de mensagens. Envio de fotos/vídeos |
| Orientação Familiar (Home Program) | 🔴 Alta | Atividades para fazer em casa, com vídeos explicativos. Família marca como "feito" e terapeuta acompanha |
| Agenda da Família | 🟡 Média | Visualização das sessões do filho, confirmação de presença, reagendamento |
| Pesquisa de Satisfação Expandida | 🟡 Média | Além do NPS: pesquisa sobre comunicação, pontualidade, evolução percebida, infraestrutura |
| Relatório Mensal para Família | 🟡 Média | Resumo automático do mês: sessões realizadas, faltas, evolução, próximos passos |

### Sprint 5: Operacional & Automações (PRIORIDADE MÉDIA)

| Item | Prioridade | Descrição |
|------|-----------|-----------|
| Lista de Espera Inteligente | 🟡 Média | Fila por área/convênio/horário. Notificação automática quando vaga abre |
| Gestão de Documentos | 🟡 Média | Upload e organização de laudos, relatórios, guias escaneadas. Vinculado ao paciente |
| Controle de Materiais/Estoque | 🟢 Baixa | Inventário de materiais terapêuticos por sala. Alerta de reposição |
| Integração com Google Agenda | 🟡 Média | Sincronização bidirecional com agenda dos terapeutas |
| Automação de Faturamento | 🟡 Média | Geração automática de fatura por convênio baseada nas sessões realizadas com guia válida |
| Conciliação Bancária | 🟢 Baixa | Importação de extrato e match com contas a receber |

### Sprint 6: Marketing & Captação (PRIORIDADE MÉDIA)

Baseado nas instruções do projeto sobre calendário editorial e marketing da Aldeia.

| Item | Prioridade | Descrição |
|------|-----------|-----------|
| Calendário Editorial Integrado | 🟡 Média | Planejamento de posts com status, responsável, data de publicação. Integração com Instagram |
| Funil de Captação de Pacientes | 🟡 Média | Lead → Triagem → Avaliação → Matrícula. Métricas de conversão por etapa |
| CRM de Famílias | 🟡 Média | Histórico de interações, follow-ups, motivo de desistência |
| Indicadores de Retenção | 🟡 Média | Churn rate, tempo médio de permanência, motivos de saída |
| Depoimentos e Cases | 🟢 Baixa | Coleta automatizada de depoimentos (pós-NPS alto). Aprovação e uso em marketing |

### Sprint 7: Relatórios & BI (PRIORIDADE MÉDIA)

| Item | Prioridade | Descrição |
|------|-----------|-----------|
| Relatório para Convênios (TISS/TUSS) | 🟡 Média | Geração no formato exigido pelos convênios para faturamento |
| Dashboard de Indicadores Clínicos | 🟡 Média | Evolução média dos pacientes por área, tempo médio para alta, taxa de evolução |
| Relatório de Absenteísmo | 🟡 Média | Faltas por paciente, por terapeuta, por dia da semana. Padrões e alertas |
| Projeção Financeira | 🟡 Média | Forecast de receita baseado em sessões agendadas, guias ativas, sazonalidade |
| Benchmark entre Áreas | 🟢 Baixa | Comparativo de produtividade, NPS, evolução entre as áreas da clínica |

---

## 3. INTEGRAÇÕES PENDENTES (Plataformas Discutidas)

| Integração | Status | Impacto |
|-----------|--------|---------|
| WhatsApp Business API (credenciais reais) | ⏳ Aguardando credenciais | Envio real de mensagens NPS e alertas de guia |
| Google Workspace (Gmail, Drive, Agenda) | ⏳ Planejado | Automação de e-mails, sincronização de agenda, documentos |
| Instagram (via MCP) | ⏳ Disponível | Publicação de posts do calendário editorial |
| Asana (via MCP) | ⏳ Disponível | Gestão de tarefas internas da equipe |
| Sistema de Convênios (TISS) | ⏳ Planejado | Envio eletrônico de guias e faturamento |
| Gateway de Pagamento | ⏳ Planejado | Cobrança automática para pacientes particulares |

---

## 4. PRIORIZAÇÃO RECOMENDADA (Próximas Sprints)

### Imediato (Sprint 2) — Foco: Retenção de Terapeutas
1. Avaliação de Desempenho 360°
2. Plano de Carreira Visual com critérios mensuráveis
3. Treinamentos e Capacitações (registro)

### Curto Prazo (Sprint 3) — Foco: Qualidade Clínica
4. Protocolos de Avaliação digitais (VB-MAPP, Denver)
5. Plano Terapêutico Individual (PTI)
6. Relatório de Evolução Automatizado para convênios

### Médio Prazo (Sprint 4) — Foco: Engajamento Familiar
7. Portal Família 2.0 com chat
8. Home Program (orientação familiar)
9. Relatório Mensal automático para família

### Médio Prazo (Sprint 5) — Foco: Eficiência Operacional
10. Lista de Espera Inteligente
11. Automação de Faturamento por convênio
12. Integração Google Agenda

### Longo Prazo (Sprint 6-7) — Foco: Crescimento
13. Funil de Captação + CRM
14. Calendário Editorial com Instagram
15. Relatórios TISS/TUSS para convênios

---

## 5. MÉTRICAS DE SUCESSO POR SPRINT

| Sprint | Métrica Principal | Meta |
|--------|------------------|------|
| Sprint 2 | Turnover de terapeutas | Reduzir de X% para Y% em 6 meses |
| Sprint 3 | Tempo para gerar relatório de evolução | De 2h manual → 5min automático |
| Sprint 4 | Engajamento familiar (acesso ao portal) | 70% das famílias acessando mensalmente |
| Sprint 5 | Tempo administrativo da recepção | Reduzir 40% com automações |
| Sprint 6 | Taxa de conversão de leads | Medir e otimizar funil |
| Sprint 7 | Glosas por convênio | Reduzir para < 1% do faturamento |

---

## 6. NOTAS DOS VÍDEOS DA LETÍCIA — PONTOS-CHAVE

1. **"A gente perde terapeuta porque não tem plano de carreira claro"** → Sprint 2 é prioridade máxima
2. **"Família que não entende o que está acontecendo desiste"** → Portal Família 2.0 e Home Program
3. **"Convênio glosa quando não tem relatório padronizado"** → Relatório automatizado + protocolos
4. **"Recepção gasta 2h por dia ligando para confirmar"** → Automação de confirmação via WhatsApp
5. **"Não sei quanto cada terapeuta gera de receita real"** → Dashboard financeiro por terapeuta (já implementado)
6. **"Guia vence e ninguém avisa a família"** → Alertas WhatsApp de guia (já implementado)
7. **"Precisamos de supervisão registrada para o convênio"** → Módulo de Supervisão Clínica

---

## 7. DECISÕES TÉCNICAS PENDENTES

| Decisão | Opções | Recomendação |
|---------|--------|--------------|
| Protocolo VB-MAPP digital | Desenvolver internamente vs. integrar com sistema existente | Desenvolver internamente (dados ficam no mesmo ecossistema) |
| Chat família-terapeuta | WebSocket em tempo real vs. mensagens assíncronas | Assíncrono (menor complexidade, suficiente para o caso de uso) |
| Faturamento TISS | Parser próprio vs. integração com sistema de convênio | Parser próprio (mais controle, independência) |
| Controle de ponto | App mobile vs. terminal na clínica | Terminal na clínica + confirmação no app (dupla validação) |

---

*Última atualização: 11 de maio de 2026*
*Autor: Manus AI para Clínica Aldeia*
