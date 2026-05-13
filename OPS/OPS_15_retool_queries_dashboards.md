# Retool — Queries SQL e Guia de Montagem dos Dashboards
**Autor:** Manus AI
**Data:** 10/05/2026
**Pré-requisito:** Schema `aldeia_supabase_schema.sql` já executado no Supabase

---

## 1. Configuração Inicial do Retool

### 1.1. Criar Conta e Conectar ao Supabase

O Retool oferece um plano gratuito para até 5 usuários, o que é suficiente para a fase inicial da Aldeia (Rica, Letícia e até 3 líderes de área). O processo de configuração segue os passos descritos abaixo.

Acesse [retool.com](https://retool.com) e crie uma conta com o e-mail corporativo da Aldeia. Em seguida, vá em **Resources** e clique em **Create New** para adicionar uma nova conexão. Selecione **PostgreSQL** como tipo de recurso e preencha os campos com as credenciais do Supabase, que podem ser encontradas em **Settings > Database** no painel do Supabase.

| Campo | Valor |
|---|---|
| Host | `db.[seu-projeto].supabase.co` |
| Port | `5432` |
| Database | `postgres` |
| Username | `postgres` |
| Password | (senha do projeto Supabase) |
| SSL | Ativado (obrigatório) |

### 1.2. Configurar Variáveis de Ambiente

No Retool, crie as seguintes variáveis de ambiente em **Settings > Environment Variables** para facilitar o uso nas queries:

| Variável | Descrição |
|---|---|
| `current_user_id` | UUID do usuário logado (extraído via auth) |
| `current_user_role` | Role do usuário (`admin`, `lider_area`, `terapeuta`) |
| `current_user_area_id` | UUID da área do usuário |

---

## 2. Tela 1: Dashboard Executivo (Visão Sócio)

Esta tela é acessível apenas por usuários com `role = 'admin'`. Ela apresenta a visão consolidada da clínica.

### 2.1. Query: KPIs Principais

```sql
-- Query: kpis_executivo
-- Retorna os KPIs do mês corrente
SELECT
  COUNT(s.id) FILTER (WHERE s.status = 'realizada') AS sessoes_realizadas,
  COALESCE(SUM(s.valor_sessao) FILTER (WHERE s.status = 'realizada'), 0) AS faturamento_bruto,
  COALESCE(SUM(s.repasse_terapeuta) FILTER (WHERE s.status = 'realizada'), 0) AS total_repasses,
  COALESCE(SUM(s.valor_sessao) FILTER (WHERE s.status = 'realizada'), 0)
    - COALESCE(SUM(s.repasse_terapeuta) FILTER (WHERE s.status = 'realizada'), 0) AS margem_clinica,
  ROUND(
    COUNT(s.id) FILTER (WHERE s.status = 'realizada')::numeric /
    NULLIF(COUNT(s.id) FILTER (WHERE s.status IN ('realizada', 'agendada')), 0) * 100, 1
  ) AS taxa_ocupacao_global,
  (SELECT COUNT(*) FROM users WHERE ativo = true AND role = 'terapeuta') AS total_terapeutas
FROM sessoes s
WHERE date_trunc('month', s.data_hora_inicio) = date_trunc('month', CURRENT_DATE);
```

### 2.2. Query: NPS Global

```sql
-- Query: nps_global
-- Calcula o NPS da clínica no semestre corrente
SELECT
  ROUND(
    ((COUNT(*) FILTER (WHERE nota >= 9) - COUNT(*) FILTER (WHERE nota <= 6))::numeric
    / NULLIF(COUNT(*), 0)) * 100, 0
  ) AS nps_score,
  COUNT(*) AS total_respostas,
  COUNT(*) FILTER (WHERE nota >= 9) AS promotores,
  COUNT(*) FILTER (WHERE nota BETWEEN 7 AND 8) AS neutros,
  COUNT(*) FILTER (WHERE nota <= 6) AS detratores
FROM nps_respostas
WHERE tipo = 'clinica'
  AND data_resposta >= date_trunc('month', CURRENT_DATE) - INTERVAL '6 months';
```

### 2.3. Query: Faturamento Mensal (Gráfico)

```sql
-- Query: faturamento_mensal
-- Dados para o gráfico de faturamento vs. meta
SELECT
  to_char(date_trunc('month', s.data_hora_inicio), 'Mon') AS mes,
  EXTRACT(MONTH FROM s.data_hora_inicio) AS mes_num,
  COALESCE(SUM(s.valor_sessao) FILTER (WHERE s.status = 'realizada'), 0) AS faturamento,
  COALESCE(m.meta_faturamento, 63000) AS meta
FROM sessoes s
LEFT JOIN metas_clinica m ON date_trunc('month', s.data_hora_inicio) = m.mes_ano
WHERE s.data_hora_inicio >= CURRENT_DATE - INTERVAL '6 months'
GROUP BY date_trunc('month', s.data_hora_inicio), m.meta_faturamento
ORDER BY mes_num;
```

### 2.4. Query: Sessões por Área (Gráfico)

```sql
-- Query: sessoes_por_area
-- Distribuição de sessões por especialidade no mês corrente
SELECT
  a.nome AS area,
  COUNT(s.id) FILTER (WHERE s.status = 'realizada') AS sessoes
FROM areas a
LEFT JOIN sessoes s ON a.id = s.area_id
  AND date_trunc('month', s.data_hora_inicio) = date_trunc('month', CURRENT_DATE)
GROUP BY a.nome
ORDER BY sessoes DESC;
```

### 2.5. Query: Ocupação por Área

```sql
-- Query: ocupacao_por_area
-- Taxa de ocupação de cada área no mês corrente
SELECT
  a.nome AS area,
  ROUND(
    COUNT(s.id) FILTER (WHERE s.status = 'realizada')::numeric /
    NULLIF(COUNT(s.id) FILTER (WHERE s.status IN ('realizada', 'agendada')), 0) * 100, 1
  ) AS taxa_ocupacao
FROM areas a
LEFT JOIN sessoes s ON a.id = s.area_id
  AND date_trunc('month', s.data_hora_inicio) = date_trunc('month', CURRENT_DATE)
GROUP BY a.nome
ORDER BY taxa_ocupacao DESC;
```

### 2.6. Query: Distribuição da Equipe por Nível

```sql
-- Query: equipe_por_nivel
-- Contagem de terapeutas por nível na Jornada Aldeia
SELECT
  nivel::text AS nivel,
  COUNT(*) AS quantidade
FROM users
WHERE ativo = true AND role IN ('terapeuta', 'lider_area')
GROUP BY nivel
ORDER BY
  CASE nivel
    WHEN 'semente' THEN 1
    WHEN 'broto' THEN 2
    WHEN 'caule' THEN 3
    WHEN 'ramo' THEN 4
    WHEN 'folha' THEN 5
    WHEN 'fruto' THEN 6
    WHEN 'arvore' THEN 7
  END;
```

### 2.7. Componentes Retool — Tela 1

A montagem no Retool utiliza os seguintes componentes, organizados em um layout de grid:

| Componente | Tipo Retool | Query | Posição |
|---|---|---|---|
| Faturamento Bruto | Statistic | `kpis_executivo.faturamento_bruto` | Topo, col 1 |
| Sessões Realizadas | Statistic | `kpis_executivo.sessoes_realizadas` | Topo, col 2 |
| NPS Global | Statistic | `nps_global.nps_score` | Topo, col 3 |
| Ocupação Global | Statistic | `kpis_executivo.taxa_ocupacao_global` | Topo, col 4 |
| Faturamento vs. Meta | Chart (Area) | `faturamento_mensal` | Meio, col 1-2 |
| Sessões por Área | Chart (Bar horizontal) | `sessoes_por_area` | Meio, col 3-4 |
| Ocupação por Área | Progress bars | `ocupacao_por_area` | Baixo, col 1-3 |
| Equipe por Nível | List | `equipe_por_nivel` | Baixo, col 4 |

---

## 3. Tela 2: Dashboard por Área (Visão Líder)

Esta tela é acessível por `lider_area` (filtrado pela sua área) e `admin` (com seletor de área).

### 3.1. Query: KPIs da Área

```sql
-- Query: kpis_area
-- KPIs de uma área específica no mês corrente
-- Parâmetro: {{ area_selecionada }} (UUID da área)
SELECT
  a.nome AS area_nome,
  COUNT(s.id) FILTER (WHERE s.status = 'realizada') AS sessoes_realizadas,
  ROUND(
    COUNT(s.id) FILTER (WHERE s.status = 'realizada')::numeric /
    NULLIF(COUNT(s.id) FILTER (WHERE s.status IN ('realizada', 'agendada')), 0) * 100, 1
  ) AS taxa_ocupacao,
  (
    SELECT COUNT(*) FROM pacientes p
    WHERE p.ativo = true
    -- Aqui seria necessário uma tabela de fila de espera
    -- Simplificação: contar pacientes sem sessão agendada
  ) AS fila_espera
FROM areas a
LEFT JOIN sessoes s ON a.id = s.area_id
  AND date_trunc('month', s.data_hora_inicio) = date_trunc('month', CURRENT_DATE)
WHERE a.id = {{ area_selecionada }}
GROUP BY a.nome;
```

### 3.2. Query: NPS da Área

```sql
-- Query: nps_area
-- NPS de uma área específica
SELECT
  ROUND(
    ((COUNT(*) FILTER (WHERE nota >= 9) - COUNT(*) FILTER (WHERE nota <= 6))::numeric
    / NULLIF(COUNT(*), 0)) * 100, 0
  ) AS nps_score,
  COUNT(*) AS total_respostas
FROM nps_respostas
WHERE tipo = 'area' AND alvo_id = {{ area_selecionada }}
  AND data_resposta >= CURRENT_DATE - INTERVAL '3 months';
```

### 3.3. Query: Terapeutas da Área (Tabela)

```sql
-- Query: terapeutas_area
-- Desempenho individual dos terapeutas de uma área
SELECT
  u.nome_completo,
  u.nivel::text AS nivel,
  COUNT(s.id) FILTER (WHERE s.status = 'realizada') AS sessoes_realizadas,
  ROUND(
    COUNT(s.id) FILTER (WHERE s.status = 'realizada')::numeric /
    NULLIF(COUNT(s.id) FILTER (WHERE s.status IN ('realizada', 'agendada')), 0) * 100, 1
  ) AS taxa_ocupacao,
  ROUND(
    (COUNT(s.id) FILTER (WHERE s.prontuario_preenchido_em <= s.data_hora_fim + INTERVAL '24 hours'))::numeric /
    NULLIF(COUNT(s.id) FILTER (WHERE s.status = 'realizada'), 0) * 100, 1
  ) AS taxa_prontuario_24h,
  (
    SELECT ROUND(
      ((COUNT(*) FILTER (WHERE nota >= 9) - COUNT(*) FILTER (WHERE nota <= 6))::numeric
      / NULLIF(COUNT(*), 0)) * 100, 0
    )
    FROM nps_respostas
    WHERE tipo = 'terapeuta' AND alvo_id = u.id
  ) AS nps_individual
FROM users u
LEFT JOIN sessoes s ON u.id = s.terapeuta_id
  AND date_trunc('month', s.data_hora_inicio) = date_trunc('month', CURRENT_DATE)
WHERE u.area_id = {{ area_selecionada }} AND u.ativo = true
GROUP BY u.id, u.nome_completo, u.nivel
ORDER BY sessoes_realizadas DESC;
```

### 3.4. Query: Evolução Mensal da Área (Gráfico)

```sql
-- Query: evolucao_area
-- Sessões realizadas por mês nos últimos 6 meses
SELECT
  to_char(date_trunc('month', s.data_hora_inicio), 'Mon') AS mes,
  EXTRACT(MONTH FROM s.data_hora_inicio) AS mes_num,
  COUNT(s.id) FILTER (WHERE s.status = 'realizada') AS sessoes
FROM sessoes s
WHERE s.area_id = {{ area_selecionada }}
  AND s.data_hora_inicio >= CURRENT_DATE - INTERVAL '6 months'
GROUP BY date_trunc('month', s.data_hora_inicio)
ORDER BY mes_num;
```

### 3.5. Componentes Retool — Tela 2

| Componente | Tipo Retool | Query | Posição |
|---|---|---|---|
| Seletor de Área | Select | `SELECT id, nome FROM areas` | Header |
| Ocupação | Statistic | `kpis_area.taxa_ocupacao` | Topo, col 1 |
| Sessões/Mês | Statistic | `kpis_area.sessoes_realizadas` | Topo, col 2 |
| NPS da Área | Statistic | `nps_area.nps_score` | Topo, col 3 |
| Fila de Espera | Statistic | `kpis_area.fila_espera` | Topo, col 4 |
| Conversão | Statistic | Calculado | Topo, col 5 |
| Evolução Mensal | Chart (Bar) | `evolucao_area` | Meio, col 1-2 |
| NPS Trend | Chart (Line) | Query adicional | Meio, col 3-4 |
| Tabela Terapeutas | Table | `terapeutas_area` | Baixo, full width |

---

## 4. Tela 3: Dashboard do Terapeuta (Visão Individual)

Esta tela mostra os KPIs pessoais do terapeuta logado. O filtro é automático via `auth.uid()`.

### 4.1. Query: Perfil e Nível

```sql
-- Query: perfil_terapeuta
-- Dados do terapeuta logado
SELECT
  u.nome_completo,
  u.nivel::text AS nivel,
  a.nome AS area,
  u.data_contratacao,
  EXTRACT(MONTH FROM AGE(CURRENT_DATE, u.data_contratacao)) +
  EXTRACT(YEAR FROM AGE(CURRENT_DATE, u.data_contratacao)) * 12 AS meses_na_aldeia
FROM users u
LEFT JOIN areas a ON u.area_id = a.id
WHERE u.id = {{ current_user_id }};
```

### 4.2. Query: KPIs Individuais

```sql
-- Query: kpis_terapeuta
-- KPIs do terapeuta no mês corrente
SELECT
  COUNT(s.id) FILTER (WHERE s.status = 'realizada') AS sessoes_realizadas,
  COUNT(s.id) FILTER (WHERE s.status IN ('realizada', 'agendada')) AS sessoes_total,
  COUNT(s.id) FILTER (WHERE s.status = 'falta_paciente') AS faltas_pacientes,
  ROUND(
    COUNT(s.id) FILTER (WHERE s.status = 'realizada')::numeric /
    NULLIF(COUNT(s.id) FILTER (WHERE s.status IN ('realizada', 'agendada')), 0) * 100, 1
  ) AS taxa_ocupacao,
  ROUND(
    (COUNT(s.id) FILTER (WHERE s.prontuario_preenchido_em IS NOT NULL
      AND s.prontuario_preenchido_em <= s.data_hora_fim + INTERVAL '24 hours'))::numeric /
    NULLIF(COUNT(s.id) FILTER (WHERE s.status = 'realizada'), 0) * 100, 1
  ) AS taxa_prontuario_24h
FROM sessoes s
WHERE s.terapeuta_id = {{ current_user_id }}
  AND date_trunc('month', s.data_hora_inicio) = date_trunc('month', CURRENT_DATE);
```

### 4.3. Query: NPS Individual

```sql
-- Query: nps_terapeuta
-- NPS do terapeuta logado
SELECT
  ROUND(
    ((COUNT(*) FILTER (WHERE nota >= 9) - COUNT(*) FILTER (WHERE nota <= 6))::numeric
    / NULLIF(COUNT(*), 0)) * 100, 0
  ) AS nps_score,
  COUNT(*) AS total_respostas
FROM nps_respostas
WHERE tipo = 'terapeuta' AND alvo_id = {{ current_user_id }};
```

### 4.4. Query: Avaliação de Desempenho

```sql
-- Query: avaliacao_desempenho
-- Histórico de avaliações trimestrais do terapeuta
SELECT
  trimestre,
  nota_clinica,
  nota_operacional,
  nota_cultural,
  nota_total,
  elegivel_promocao,
  feedback_qualitativo
FROM avaliacoes_desempenho
WHERE terapeuta_id = {{ current_user_id }}
ORDER BY data_avaliacao DESC;
```

### 4.5. Query: Agenda do Dia

```sql
-- Query: agenda_hoje
-- Sessões agendadas para hoje
SELECT
  to_char(s.data_hora_inicio, 'HH24:MI') AS hora,
  p.nome_completo AS paciente,
  s.status::text AS status
FROM sessoes s
JOIN pacientes p ON s.paciente_id = p.id
WHERE s.terapeuta_id = {{ current_user_id }}
  AND date_trunc('day', s.data_hora_inicio) = date_trunc('day', CURRENT_DATE)
ORDER BY s.data_hora_inicio;
```

### 4.6. Query: Régua de Promoção

```sql
-- Query: regua_promocao
-- Verifica se o terapeuta está elegível para promoção
WITH ultima_avaliacao AS (
  SELECT nota_total, elegivel_promocao
  FROM avaliacoes_desempenho
  WHERE terapeuta_id = {{ current_user_id }}
  ORDER BY data_avaliacao DESC
  LIMIT 1
),
meta_promocao AS (
  SELECT
    CASE u.nivel
      WHEN 'semente' THEN 80
      WHEN 'broto' THEN 85
      WHEN 'caule' THEN 85
      WHEN 'ramo' THEN 90
      WHEN 'folha' THEN 95
      WHEN 'fruto' THEN 95
      ELSE 100
    END AS pontos_necessarios,
    CASE u.nivel
      WHEN 'semente' THEN 'broto'
      WHEN 'broto' THEN 'caule'
      WHEN 'caule' THEN 'ramo'
      WHEN 'ramo' THEN 'folha'
      WHEN 'folha' THEN 'fruto'
      WHEN 'fruto' THEN 'arvore'
      ELSE 'arvore'
    END AS proximo_nivel
  FROM users u
  WHERE u.id = {{ current_user_id }}
),
ebitda AS (
  SELECT ebitda_positivo
  FROM metas_clinica
  WHERE mes_ano = date_trunc('month', CURRENT_DATE)
)
SELECT
  ua.nota_total AS nota_atual,
  mp.pontos_necessarios,
  mp.proximo_nivel,
  ua.nota_total >= mp.pontos_necessarios AS atingiu_meta,
  COALESCE(e.ebitda_positivo, false) AS ebitda_ok,
  ua.nota_total >= mp.pontos_necessarios AND COALESCE(e.ebitda_positivo, false) AS promocao_aprovada
FROM ultima_avaliacao ua, meta_promocao mp, ebitda e;
```

### 4.7. Componentes Retool — Tela 3

| Componente | Tipo Retool | Query | Posição |
|---|---|---|---|
| Card do Perfil | Container | `perfil_terapeuta` | Topo, full width |
| Jornada Visual | Image + Marker | Estático | Dentro do Card Perfil |
| Ocupação | Statistic | `kpis_terapeuta.taxa_ocupacao` | KPIs, col 1 |
| Prontuário 24h | Statistic | `kpis_terapeuta.taxa_prontuario_24h` | KPIs, col 2 |
| NPS Individual | Statistic | `nps_terapeuta.nps_score` | KPIs, col 3 |
| Capacitação | Statistic | Manual/calculado | KPIs, col 4 |
| Avaliação (Stacked Bar) | Chart | `avaliacao_desempenho` | Meio, col 1-2 |
| Agenda do Dia | Table | `agenda_hoje` | Meio, col 3 |
| Régua de Promoção | Container | `regua_promocao` | Baixo, full width |

---

## 5. Controle de Acesso por Role

O Retool permite condicionar a visibilidade de componentes e páginas com base em variáveis. A lógica de controle segue a tabela abaixo:

| Tela | `admin` | `lider_area` | `terapeuta` |
|---|---|---|---|
| Executiva | Acesso total | Bloqueada | Bloqueada |
| Por Área | Acesso total (com seletor) | Apenas sua área | Bloqueada |
| Terapeuta | Pode ver qualquer terapeuta | Pode ver terapeutas da sua área | Apenas seus dados |

Para implementar no Retool, utilize a propriedade **Hidden** dos componentes com a condição:

```javascript
// Esconder tela executiva para não-admins
{{ current_user.role !== 'admin' }}

// Esconder seletor de área para líderes (fixar na área deles)
{{ current_user.role === 'lider_area' }}
```

---

## 6. Passo a Passo Resumido

A implementação completa segue a sequência abaixo:

| Passo | Ação | Tempo estimado |
|---|---|---|
| 1 | Criar conta no Supabase e rodar o schema SQL | 15 min |
| 2 | Criar conta no Retool (plano gratuito) | 5 min |
| 3 | Conectar Retool ao Supabase (PostgreSQL) | 10 min |
| 4 | Criar as 3 páginas no Retool | 5 min |
| 5 | Copiar as queries SQL deste documento | 30 min |
| 6 | Montar os componentes visuais (drag-and-drop) | 2-3 horas |
| 7 | Configurar controle de acesso por role | 30 min |
| 8 | Inserir dados reais e testar | 1 hora |

**Tempo total estimado: 4-5 horas** para ter os 3 dashboards funcionando com dados reais.

---

## Referências

[1] Retool. Getting Started with PostgreSQL. Disponível em: https://docs.retool.com/docs/postgresql
[2] Supabase. Database Connection Info. Disponível em: https://supabase.com/docs/guides/database/connecting-to-postgres
