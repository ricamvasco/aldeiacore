# Análise do Vídeo 1 — Reunião com Letícia (Sistema Atual)

## Resumo
Letícia (sócia) demonstra o sistema de gestão de clínica que utiliza atualmente, apontando funcionalidades, fluxos de trabalho e diversas críticas.

---

## 1) Telas e Funcionalidades do Sistema Mostrado

- **Tela de Evolução (Prontuário):** Caixa de texto livre onde o terapeuta descreve o que aconteceu na sessão. Campos: Nome do paciente (bloqueado), Especialidade, Status (Realizada/Cancelamento/Falta), Quem cancelou, Motivo.
- **Tela de Metas:** Interface com protocolos (VB-MAPP, Denver) onde marca "Sim" ou "Não" para cada meta da criança.
- **Relatório de Pagamento:** Gráfico de pizza com total de atendimentos realizados (549), cancelados (112), faltas (115).
- **Perfil do Paciente:** Informações clínicas (diagnóstico, comorbidades, medicação), contatos dos responsáveis.
- **Jornada do Paciente no Dia:** Visualização de quem atende antes e depois.
- **Anexos/Feedback:** Área para anexar documentos (feedbacks assinados, relatórios).

---

## 2) Fluxos de Trabalho Demonstrados

- **Fluxo de Evolução:** Terapeuta seleciona paciente → seleciona especialidade → preenche caixa de texto livre → salva.
- **Fluxo de Metas:** Terapeuta seleciona protocolo (ex: VB-MAPP) → seleciona meta (ex: "Ecolalia/Ecoico") → marca "Sim" ou "Não".
- **Fluxo de Relatório para Convênio (FUSEX):** Sistema só tem texto livre → exporta para Excel → cria fórmulas para filtrar → envia ao convênio. FLUXO QUEBRADO.
- **Fluxo de Feedback aos Pais:** Terapeuta escreve feedback → imprime → pais assinam fisicamente → clínica fotografa → anexa na aba "Outros". FLUXO ANALÓGICO.

---

## 3) Campos e Dados Visíveis nas Telas

- **Evolução:** Nome paciente, Especialidade (Psicologia GDS), Status, Quem cancelou, Motivo, Texto livre.
- **Metas:** Nome do programa/protocolo, Nome da meta, Botões Sim/Não.
- **Relatório Pagamento:** Gráfico pizza, Total atendimentos, Cancelados, Faltas.
- **Perfil Paciente (Liz):** Diagnóstico principal, comorbidades, medicação (VAZIOS), Contatos (responsável, CPF, profissão, telefone, e-mail).

---

## 4) O que Letícia Explica Verbalmente

- **Sobre Evolução (Texto Livre):** Ter apenas texto aberto é PÉSSIMO para extrair dados. Sugere campos fechados (checkboxes) para "Estado geral do paciente" (adequado, irritado) e "Objetivo da terapia". Só "Respostas do paciente" deveria ser texto livre.
- **Sobre Especialidade:** Ter que selecionar toda vez é perda de tempo — sistema deveria saber quem ela é.
- **Sobre Metas:** Só permite Sim/Não. Detalhes qualitativos vai para texto livre, gerando retrabalho e desconexão.
- **Sobre Pastas Físicas:** Usa pasta física porque supervisora exige.
- **Sobre Relatório de Pagamento:** NÃO SERVE para ela. Sistema calcula por sessão, mas ela recebe por HORA (R$ 120/hora). Precisa contar dias manualmente.
- **Sobre Perfil do Paciente:** Informações Clínicas VAZIAS. Se terapeuta nova atender, não sabe diagnóstico nem medicações. Recepção não preenche e terapeutas não têm permissão para editar.
- **Sobre Anexos:** Nomes genéricos (ex: "Feedback 2023"). Impossível saber data ou autor sem baixar.

---

## 5) Pontos Positivos e Negativos

### Positivos:
- Ver jornada do paciente no dia (quem atende antes/depois)
- Histórico de evoluções de outros terapeutas
- Protocolos integrados (VB-MAPP, Denver)

### Negativos (CRÍTICOS):
1. **Falta de campos estruturados** — texto livre impede relatórios automáticos, gera trabalho manual no Excel para convênios
2. **Lentidão e Bugs** — sistema trava frequentemente
3. **Falta de Assinatura Digital** — processo de feedback exige imprimir/assinar/fotografar
4. **Informações Clínicas Vazias** — dados vitais indisponíveis para equipe multidisciplinar
5. **Desconexão de Dados** — Metas (Sim/Não) não conversa com Evolução (texto)
6. **Dashboard Financeiro Inútil** — calcula por sessão, mas modelo é por hora
7. **Retrabalho** — preencher especialidade a cada evolução
8. **Organização de Anexos Ruim** — nomes genéricos, sem data/autor

---

## Requisitos para a Plataforma Aldeia (extraídos do vídeo)

1. Evolução com campos ESTRUTURADOS (estado geral, objetivo, respostas — apenas último em texto livre)
2. Metas conectadas à evolução (dados quantitativos + qualitativos no mesmo lugar)
3. Assinatura digital para feedback aos pais
4. Perfil do paciente COMPLETO e editável por terapeutas
5. Relatório automático para convênios (sem exportar para Excel)
6. Simulador de ganhos que suporte modelo por HORA (não só por sessão)
7. Sistema rápido, sem travamentos
8. Anexos com metadados (data, autor, tipo)
9. Especialidade auto-preenchida baseada no perfil do terapeuta
10. Jornada do paciente no dia (quem atende antes/depois)
