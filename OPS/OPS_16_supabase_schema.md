# Supabase Schema — Aldeia Core (Documentação)
**Autor:** Manus AI
**Data:** 10/05/2026
**Arquivo SQL:** `aldeia_supabase_schema.sql`
**Status:** Testado e validado em PostgreSQL 14

---

## 1. Visão Geral

O schema "Aldeia Core" é o banco de dados que sustenta os dashboards de KPIs, as avaliações de desempenho e o sistema de NPS da Aldeia. Ele foi projetado para rodar no **Supabase** (PostgreSQL gerenciado) e possui **Row-Level Security (RLS)** nativo, garantindo que cada usuário veja apenas os dados pertinentes ao seu perfil.

### Diagrama de Relacionamento (Entidade-Relacionamento)

```
areas ──────────┐
                │
users ──────────┤──── sessoes ──── pacientes
                │         │
                │    nps_respostas
                │
avaliacoes_desempenho
                │
metas_clinica (independente)
```

---

## 2. Tabelas

### 2.1. `areas` — Áreas de Especialização

Armazena as especialidades da clínica. Já vem populada com 5 áreas iniciais.

| Coluna | Tipo | Descrição |
|---|---|---|
| `id` | UUID (PK) | Identificador único |
| `nome` | VARCHAR(100) | Nome da área (ex: "Fonoaudiologia") |
| `created_at` | TIMESTAMP | Data de criação |

**Dados iniciais (atualizados 16/05/2026):** Neuropsicologia, Pedagogia, Psicologia, Fonoaudiologia, Terapia Ocupacional, Psicomotricidade, Integração Sensorial.

> ⚠️ **Nota de arquitetura (16/05/2026):** Musicoterapia foi removida — não é uma especialidade da Aldeia. As atividades complementares (Jiu-jitsu, Judô, Botânica, Circo) devem ser tratadas como categoria separada no banco (`tipo = 'atividade_complementar'`), pois contribuem para as metas das disciplinas clínicas mas não são especialidades terapêuticas formais. Requer task de arquitetura para atualizar o ENUM `areas` e criar coluna `tipo` na tabela.

### 2.2. `users` — Usuários do Sistema

Estende a tabela `auth.users` do Supabase (autenticação). Cada terapeuta, líder e sócio tem um registro aqui.

| Coluna | Tipo | Descrição |
|---|---|---|
| `id` | UUID (PK, FK → auth.users) | Mesmo ID do login do Supabase |
| `nome_completo` | VARCHAR(255) | Nome do profissional |
| `email` | VARCHAR(255) | E-mail (login) |
| `role` | ENUM | `admin`, `lider_area` ou `terapeuta` |
| `nivel` | ENUM | Nível na Jornada Aldeia: `semente` a `arvore` |
| `area_id` | UUID (FK → areas) | Área de atuação (nulo para admins) |
| `data_contratacao` | DATE | Data de início na Aldeia |
| `ativo` | BOOLEAN | Se o profissional está ativo |

**Roles e o que cada um vê:**

| Role | Quem é | O que vê no dashboard |
|---|---|---|
| `admin` | Rica e Letícia | Tudo: clínica, todas as áreas, todos os terapeutas |
| `lider_area` | Terapeuta Fruto/Árvore | Sua área + terapeutas da sua área |
| `terapeuta` | Demais terapeutas | Apenas seus próprios dados |

### 2.3. `pacientes` — Cadastro de Pacientes

| Coluna | Tipo | Descrição |
|---|---|---|
| `id` | UUID (PK) | Identificador único |
| `nome_completo` | VARCHAR(255) | Nome da criança |
| `data_nascimento` | DATE | Data de nascimento |
| `nome_responsavel` | VARCHAR(255) | Nome do pai/mãe |
| `email_responsavel` | VARCHAR(255) | E-mail para envio de NPS |
| `telefone_responsavel` | VARCHAR(20) | WhatsApp |
| `ativo` | BOOLEAN | Se o paciente está em tratamento |

### 2.4. `sessoes` — Atendimentos

A tabela mais importante. Cada linha é uma sessão agendada ou realizada.

| Coluna | Tipo | Descrição |
|---|---|---|
| `id` | UUID (PK) | Identificador único |
| `terapeuta_id` | UUID (FK → users) | Quem atendeu |
| `paciente_id` | UUID (FK → pacientes) | Quem foi atendido |
| `area_id` | UUID (FK → areas) | Qual especialidade |
| `data_hora_inicio` | TIMESTAMP | Início da sessão |
| `data_hora_fim` | TIMESTAMP | Fim da sessão |
| `status` | ENUM | `agendada`, `realizada`, `falta_paciente`, `falta_terapeuta`, `cancelada` |
| `valor_sessao` | DECIMAL | Valor cobrado (particular ou convênio) |
| `repasse_terapeuta` | DECIMAL | Valor repassado ao terapeuta |
| `prontuario_preenchido_em` | TIMESTAMP | Quando o prontuário foi preenchido (para medir SLA 24h) |

### 2.5. `nps_respostas` — Pesquisas de Satisfação

Armazena as respostas de NPS nos 3 níveis (clínica, área, terapeuta).

| Coluna | Tipo | Descrição |
|---|---|---|
| `id` | UUID (PK) | Identificador único |
| `paciente_id` | UUID (FK → pacientes) | Quem respondeu |
| `tipo` | ENUM | `clinica`, `area` ou `terapeuta` |
| `alvo_id` | UUID | ID da área ou do terapeuta avaliado (nulo se tipo = clinica) |
| `nota` | INTEGER (0-10) | Nota do NPS |
| `comentario` | TEXT | Feedback qualitativo |
| `data_resposta` | TIMESTAMP | Quando respondeu |

**Como calcular o NPS a partir desta tabela:**

> NPS = ((Promotores - Detratores) / Total de Respostas) x 100
>
> Promotores = nota 9 ou 10 | Neutros = nota 7 ou 8 | Detratores = nota 0 a 6

### 2.6. `avaliacoes_desempenho` — Scoring Trimestral

Armazena a avaliação de cada terapeuta a cada trimestre. A `nota_total` é calculada automaticamente pelo banco.

| Coluna | Tipo | Descrição |
|---|---|---|
| `id` | UUID (PK) | Identificador único |
| `terapeuta_id` | UUID (FK → users) | Quem foi avaliado |
| `avaliador_id` | UUID (FK → users) | Quem avaliou |
| `trimestre` | VARCHAR(10) | Ex: "2026-Q3" |
| `nota_clinica` | INTEGER (0-40) | Pilar 1: Desempenho Clínico |
| `nota_operacional` | INTEGER (0-30) | Pilar 2: Desempenho Operacional |
| `nota_cultural` | INTEGER (0-30) | Pilar 3: Fit Cultural |
| `nota_total` | INTEGER (0-100) | **Calculado automaticamente** (soma dos 3 pilares) |
| `elegivel_promocao` | BOOLEAN | Se atingiu a pontuação mínima para promoção |
| `feedback_qualitativo` | TEXT | Comentários do avaliador |

**Constraint:** Apenas uma avaliação por terapeuta por trimestre (UNIQUE).

### 2.7. `metas_clinica` — Metas Mensais da Clínica

Tabela de referência para comparar o realizado vs. planejado no dashboard executivo.

| Coluna | Tipo | Descrição |
|---|---|---|
| `id` | UUID (PK) | Identificador único |
| `mes_ano` | DATE | Mês de referência (ex: 2026-07-01) |
| `meta_faturamento` | DECIMAL | Meta de faturamento bruto |
| `meta_sessoes` | INTEGER | Meta de sessões realizadas |
| `ebitda_positivo` | BOOLEAN | Se a clínica está com EBITDA positivo (gatilho para promoções) |

---

## 3. Views (Consultas Prontas para Dashboards)

### 3.1. `vw_dashboard_terapeuta`
Retorna os KPIs individuais do terapeuta no mês corrente.

| Campo | O que mostra |
|---|---|
| `terapeuta_id` | ID do terapeuta |
| `nome_completo` | Nome |
| `nivel` | Nível na Jornada Aldeia |
| `sessoes_realizadas` | Total de sessões realizadas no mês |
| `faltas_pacientes` | Total de faltas de pacientes no mês |
| `taxa_prontuario_24h` | % de prontuários preenchidos em até 24h |
| `nps_score` | NPS individual do terapeuta |

### 3.2. `vw_dashboard_clinica`
Retorna os KPIs da clínica agrupados por mês.

| Campo | O que mostra |
|---|---|
| `mes` | Mês de referência |
| `total_sessoes` | Total de sessões realizadas |
| `faturamento_bruto` | Receita total |
| `total_repasses` | Total pago aos terapeutas |
| `margem_clinica` | Faturamento - Repasses |

---

## 4. Row-Level Security (RLS)

Todas as tabelas têm RLS habilitado. As políticas garantem:

| Tabela | Terapeuta vê | Líder de Área vê | Admin vê |
|---|---|---|---|
| `sessoes` | Apenas suas sessões | Sessões da sua área | Todas |
| `avaliacoes_desempenho` | Apenas suas avaliações | Avaliações da sua área | Todas |
| `nps_respostas` | Apenas NPS sobre ele | NPS da sua área | Todos |
| `users` | Todos (leitura) | Todos (leitura) | Todos (leitura + escrita) |

---

## 5. Triggers (Automações)

O trigger `update_updated_at_column` atualiza automaticamente o campo `updated_at` nas tabelas `users` e `sessoes` sempre que um registro é modificado.

---

## 6. Como Rodar no Supabase

1. Acesse o **Supabase Dashboard** → seu projeto → **SQL Editor**
2. Cole o conteúdo do arquivo `aldeia_supabase_schema.sql`
3. Clique em **Run**
4. Verifique no **Table Editor** se as 7 tabelas foram criadas
5. Verifique em **Authentication → Policies** se as políticas RLS estão ativas

---

## 7. Resultado dos Testes

O schema foi testado em PostgreSQL 14 local com os seguintes resultados:

| Teste | Resultado |
|---|---|
| Criação de todas as tabelas | OK |
| Criação de todos os enums | OK |
| Criação das views | OK |
| Criação dos triggers | OK |
| Inserção de dados com integridade referencial | OK |
| Cálculo automático da `nota_total` (35+28+27=90) | OK |
| View `vw_dashboard_terapeuta` retornando dados | OK |
| View `vw_dashboard_clinica` retornando dados | OK |
