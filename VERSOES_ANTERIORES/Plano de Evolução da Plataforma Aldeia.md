# Plano de Evolução da Plataforma Aldeia
## Baseado na Análise dos Vídeos da Reunião com Letícia

---

## Diagnóstico: O que o sistema atual faz mal

| Problema | Impacto | Prioridade |
|----------|---------|------------|
| Evolução em texto livre (sem campos estruturados) | Impossível gerar relatórios automáticos para convênios | CRÍTICA |
| Sem gestão de guias/convênios | Perda de faturamento, risco legal, pais insatisfeitos | CRÍTICA |
| Sem alertas de vencimento de guia | Atendimentos sem cobertura, prejuízo financeiro | CRÍTICA |
| Metas desconectadas da evolução | Retrabalho, dados fragmentados | ALTA |
| Dashboard financeiro por sessão (não por hora) | Terapeuta não sabe quanto vai ganhar | ALTA |
| Informações clínicas vazias/não editáveis | Risco clínico para paciente | ALTA |
| Feedback aos pais analógico (imprimir/assinar/fotografar) | Ineficiência, perda de tempo | MÉDIA |
| Anexos com nomes genéricos | Impossível buscar por data/autor | MÉDIA |
| Especialidade preenchida manualmente a cada evolução | Perda de tempo | BAIXA |

---

## O que a Plataforma Aldeia JÁ TEM vs. O que PRECISA EVOLUIR

### Já temos:
- [x] Dashboard Executivo com KPIs
- [x] Cadastro de Pacientes
- [x] Cadastro de Colaboradores/Terapeutas
- [x] Prontuário Digital (básico)
- [x] Simulador de Ganhos (7 níveis Semente→Árvore)
- [x] Gestão de Salas
- [x] Agenda Visual
- [x] Módulo Financeiro (DRE, contas a receber, comissionamento)
- [x] Portal da Família
- [x] NPS + QR Code + WhatsApp
- [x] Relatórios PDF
- [x] Notificações
- [x] Exportação iCal

### Precisa evoluir (extraído dos vídeos):

#### PRIORIDADE CRÍTICA (Bloqueia operação)
1. **Módulo de Gestão de Guias/Convênios**
   - Cadastro de guias por paciente (número, validade, plano)
   - Dashboard de guias próximas do vencimento
   - Alertas automáticos para pais (30 dias antes, 15 dias, 7 dias)
   - Alertas para administração
   - Bloqueio inteligente: aviso ANTES do atendimento se guia inválida
   - Fluxo de renovação com checklist

2. **Evolução com Campos Estruturados**
   - Estado geral do paciente (checkboxes: adequado, irritado, sonolento, etc.)
   - Objetivo da terapia (select/checkbox vinculado às metas)
   - Respostas do paciente (texto livre — ÚNICO campo aberto)
   - Vinculação automática com metas marcadas na sessão
   - Auto-preenchimento de especialidade baseado no perfil do terapeuta

3. **Relatório Automático para Convênios**
   - Geração automática de relatório no formato exigido pelo convênio (FUSEX, Unimed, etc.)
   - Sem necessidade de exportar para Excel
   - Filtros por período, paciente, objetivo

#### PRIORIDADE ALTA (Melhora significativa)
4. **Metas Conectadas à Evolução**
   - Tela de metas com Sim/Não + campo qualitativo
   - Dados da meta aparecem automaticamente na evolução
   - Protocolos integrados (VB-MAPP, Denver, ABLLS-R)
   - Gráfico de progresso por meta ao longo do tempo

5. **Perfil do Paciente Completo**
   - Informações clínicas OBRIGATÓRIAS (diagnóstico, comorbidades, medicação)
   - Editável por terapeutas (com log de alterações)
   - Jornada do paciente no dia (quem atende antes/depois)
   - Histórico de evoluções de todos os terapeutas

6. **Simulador de Ganhos por HORA**
   - Além do modelo por sessão, suportar modelo por hora
   - Terapeuta escolhe seu modelo de remuneração
   - Cálculo automático baseado em horas trabalhadas

#### PRIORIDADE MÉDIA (Melhora experiência)
7. **Assinatura Digital**
   - Feedback aos pais com assinatura digital (touch/mouse)
   - Eliminar processo de imprimir/assinar/fotografar
   - Armazenamento com metadados (data, autor, tipo)

8. **Notificações Push Multicanal**
   - Alertas no portal dos pais
   - Alertas via WhatsApp
   - Alertas no painel administrativo
   - Configurável por tipo (guia, meta, falta, etc.)

9. **Gestão de Anexos Inteligente**
   - Upload com metadados automáticos (data, autor, tipo, paciente)
   - Busca por data, autor, tipo de documento
   - Organização por categorias

---

## Roadmap de Implementação Sugerido

### Sprint 1 (Próxima): Gestão de Guias + Alertas
- Tabela de guias no banco
- CRUD de guias por paciente
- Dashboard de vencimentos
- Alertas automáticos (portal + WhatsApp)
- Bloqueio pré-atendimento

### Sprint 2: Evolução Estruturada + Metas
- Refatorar prontuário com campos estruturados
- Conectar metas à evolução
- Integrar protocolos (VB-MAPP, Denver)
- Auto-preenchimento de especialidade

### Sprint 3: Relatórios para Convênios + Assinatura Digital
- Templates de relatório por convênio
- Geração automática
- Assinatura digital no feedback
- Gestão de anexos com metadados

### Sprint 4: Perfil Completo + Financeiro por Hora
- Perfil do paciente obrigatório
- Jornada do paciente no dia
- Modelo de remuneração por hora no simulador
- Comissionamento por hora

---

## Decisões de Negócio Confirmadas (para Banco de Decisões)

1. Letícia recebe por HORA (R$ 120/hora), não por sessão
2. Guias vencem a cada 4-6 meses dependendo do plano
3. Convênios atendidos: FUSEX, Unimed (pelo menos)
4. Não se faz evolução retroativa — integridade do registro é inegociável
5. Protocolos usados: VB-MAPP, Denver
6. Supervisora exige pasta física (mas sistema digital deve coexistir)
7. Feedback aos pais requer assinatura (hoje física, migrar para digital)
