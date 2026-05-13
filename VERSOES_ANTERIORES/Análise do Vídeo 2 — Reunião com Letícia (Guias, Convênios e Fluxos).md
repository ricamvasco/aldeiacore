# Análise do Vídeo 2 — Reunião com Letícia (Guias, Convênios e Fluxos)

## Resumo
Letícia relata problemas graves de fluxo de trabalho relacionados à autorização de planos de saúde (guias) e à comunicação entre recepção/administração, terapeutas e pais.

---

## 1) Problemas Identificados

### Fluxo Problemático de Evolução + Guias

- **O Problema:** Pacientes são atendidos mas estão "sem guia" (sem autorização do plano liberada no sistema)
- **A "Solução" da Clínica (que ela recusa):** Administração pede para colocar "cancelamento" no dia real → depois, quando guia é liberada em dia aleatório, pede para registrar evolução como se criança estivesse lá naquele momento
- **Recusa Ética/Legal:** Letícia se recusa — "Se a criança não está comigo naquele horário, eu não evoluo". Teme problemas legais
- **Exemplo:** Quarta-feira paciente Unimed faltou → clínica mandou retirar evolução e colocar "falta sem guia" → quinta à noite avisou que guia foi liberada e pediu para "evoluir agora" → ela não fez
- **Risco:** Se registrar falsamente que criança estava em terapia e nesse horário criança sofrer acidente, plano questionará

### Fluxo de Renovação de Guias

- Guias vencem a cada 4 ou 6 meses dependendo do plano
- **Não há nenhum aviso prévio** — pais esquecem de renovar
- **Consequência:** Clínica manda pais embora sem atendimento → pais ficam "muito putos"
- **Prejuízo Financeiro:** Letícia pagou do próprio bolso atendimento de uma menina em terapia de grupo por falta de guia

### Fluxo de Agendamento

- Quando paciente sai da agenda e abre vaga, comunicação gera conflitos entre pais e equipe de agendamento
- Vídeo corta antes de concluir

---

## 2) Pontos Negativos do Sistema/Processo Atual

1. **Falta de automação e alertas** — sistema não avisa quando guia está para vencer
2. **Risco Legal e Ético** — fluxo exige registros retroativos em dias falsos
3. **Falha de Comunicação Interna** — recepção não avisa terapeuta ANTES da consulta que paciente está sem guia
4. **Impacto no Cliente (Pais)** — mandados embora na porta, cobrados em cima da hora
5. **Impacto Financeiro no Terapeuta** — risco de não receber por atendimentos sem guia
6. **Falta de Proatividade** — notificações precisam ser "push", não depender de alguém procurar

---

## 3) Sugestões de Melhorias (O que o novo sistema DEVE ter)

1. **Sistema de Alertas de Vencimento de Guia** — PRIORIDADE #1
   - Aviso automático quando guia está prestes a vencer
   - Notificação para pais E para administração
   - "Você tem mais um mês de atendimento autorizado"

2. **Notificações Multicanal**
   - Aviso no app/portal dos pais
   - Aviso na área administrativa
   - Idealmente via WhatsApp também

3. **Bloqueio de Evolução sem Guia Válida**
   - Sistema não deve permitir registrar evolução se guia não está ativa
   - Alerta ANTES do atendimento (não depois)

4. **Gestão de Guias/Convênios**
   - Cadastro de guias por paciente com data de validade
   - Dashboard de guias próximas do vencimento
   - Fluxo de renovação com checklist

5. **Responsabilidade Comercial Automatizada**
   - Sistema gerencia avisos para não perder faturamento
   - Proativo em lembrar pais sobre renovação

---

## Requisitos para a Plataforma Aldeia (extraídos do vídeo 2)

1. **Módulo de Gestão de Guias/Convênios** com alertas automáticos de vencimento
2. **Notificações push multicanal** (app + WhatsApp + painel admin)
3. **Bloqueio inteligente** — não permitir evolução sem guia válida, com alerta ANTES do atendimento
4. **Dashboard de guias** — visão de todas as guias próximas do vencimento
5. **Fluxo de renovação** — checklist automatizado para pais e administração
6. **Registro de evolução com integridade** — não permitir registros retroativos fraudulentos
7. **Comunicação proativa com pais** — lembretes automáticos de renovação
