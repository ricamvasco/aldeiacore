# TASK DE ARQUITETURA — Atualização de Especialidades no Banco

**Criado em:** 16/05/2026  
**Prioridade:** P1 (Alta — deve ser feito antes da migração de dados reais)  
**Status:** ⏳ Pendente

---

## Contexto

Em sessão de 16/05/2026, Rica confirmou as especialidades definitivas da Aldeia. A tabela `areas` no banco de dados Supabase contém dados incorretos (incluía Musicoterapia, que não é uma especialidade da Aldeia).

---

## Especialidades Clínicas Definitivas (7)

| # | Especialidade | Tipo |
|---|---|---|
| 1 | Neuropsicologia | Clínica |
| 2 | Pedagogia | Clínica |
| 3 | Psicologia | Clínica |
| 4 | Fonoaudiologia | Clínica |
| 5 | Terapia Ocupacional | Clínica |
| 6 | Psicomotricidade | Clínica |
| 7 | Integração Sensorial | Clínica |

## Atividades Complementares (vetores de desenvolvimento)

| # | Atividade | Conecta com |
|---|---|---|
| 1 | Jiu-jitsu | Psicomotricidade, TO, Psicologia |
| 2 | Judô | Psicomotricidade, TO, Psicologia |
| 3 | Botânica | Pedagogia, Neuropsicologia |
| 4 | Circo | Psicomotricidade, Integração Sensorial, TO |

---

## Mudanças Necessárias no Banco

### 1. Adicionar coluna `tipo` na tabela `areas`
```sql
ALTER TABLE areas 
ADD COLUMN tipo VARCHAR(50) DEFAULT 'clinica' 
CHECK (tipo IN ('clinica', 'atividade_complementar'));
```

### 2. Atualizar dados iniciais da tabela `areas`
```sql
-- Remover Musicoterapia
DELETE FROM areas WHERE nome = 'Musicoterapia';

-- Inserir especialidades corretas
INSERT INTO areas (nome, tipo) VALUES
  ('Neuropsicologia', 'clinica'),
  ('Pedagogia', 'clinica'),
  ('Psicologia', 'clinica'),
  ('Fonoaudiologia', 'clinica'),
  ('Terapia Ocupacional', 'clinica'),
  ('Psicomotricidade', 'clinica'),
  ('Integração Sensorial', 'clinica'),
  ('Jiu-jitsu', 'atividade_complementar'),
  ('Judô', 'atividade_complementar'),
  ('Botânica', 'atividade_complementar'),
  ('Circo', 'atividade_complementar')
ON CONFLICT (nome) DO NOTHING;
```

### 3. Atualizar Dashboard por Área na plataforma
O componente de Dashboard por Área atualmente lista: Fono, TO, Psico, Neuro.  
Deve ser atualizado para listar todas as 7 especialidades clínicas.

### 4. Futura task — Metas 360 por Especialidade
Esta task está conectada ao desenvolvimento do **Método Aldeia 360**, que requer que cada paciente possa ter metas vinculadas a múltiplas especialidades simultaneamente. A estrutura de `areas` com `tipo` é o pré-requisito para isso.

---

## Impacto

| Componente | Impacto | Ação |
|---|---|---|
| `areas` (tabela) | Dados incorretos | Corrigir via SQL |
| Dashboard por Área | Mostra apenas 4 áreas | Atualizar componente |
| Cadastro de Colaboradores | Campo `area_id` | Sem impacto (FK dinâmica) |
| Relatórios | Agrupamento por área | Sem impacto (dinâmico) |
| Metas 360 (futuro) | Depende desta correção | Bloqueia desenvolvimento |

---

## Responsável
Manus (desenvolvimento) — executar na próxima sprint de plataforma.
