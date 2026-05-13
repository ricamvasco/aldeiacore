# Aldeia — Próximos Passos: Supabase e Dashboards em Produção

**Data:** 10/05/2026
**Status:** Conta Supabase criada, schema SQL pronto, dashboard protótipo funcional

---

## Visão Geral

Este documento detalha o passo a passo para transformar o protótipo dos dashboards da Aldeia em um sistema de produção conectado ao Supabase, com dados reais e autenticação. O processo está dividido em 5 etapas sequenciais.

---

## Etapa 1 — Configurar o Projeto no Supabase (15 min)

Agora que a conta foi criada, o próximo passo é criar o projeto e rodar o schema SQL.

**Passo a passo:**

1. Acesse [app.supabase.com](https://app.supabase.com) e clique em **"New Project"**
2. Preencha:
   - **Name:** `aldeia-core`
   - **Database Password:** crie uma senha forte e guarde em lugar seguro
   - **Region:** South America (São Paulo) — `sa-east-1`
3. Aguarde ~2 minutos para o projeto ser provisionado
4. Vá em **SQL Editor** (menu lateral esquerdo)
5. Clique em **"New Query"**
6. Cole o conteúdo completo do arquivo `aldeia_supabase_schema.sql` que já te entreguei
7. Clique em **"Run"**
8. Todas as tabelas, views, políticas RLS e triggers serão criados automaticamente

**Verificação:** Vá em **Table Editor** e confirme que as 7 tabelas apareceram: `areas`, `users`, `pacientes`, `sessoes`, `nps_respostas`, `avaliacoes_desempenho`, `metas_clinica`.

---

## Etapa 2 — Configurar Autenticação (20 min)

O Supabase já vem com autenticação pronta. Precisamos apenas configurar os provedores.

**Passo a passo:**

1. Vá em **Authentication > Providers**
2. Ative o provedor **Email** (já vem ativo por padrão)
3. Em **Authentication > URL Configuration**, defina:
   - **Site URL:** a URL do seu dashboard (será definida quando publicarmos)
   - **Redirect URLs:** adicione `http://localhost:3000` para desenvolvimento
4. Crie os primeiros usuários manualmente:
   - Vá em **Authentication > Users > Add User**
   - Crie: `rica@aldeia.com.br` (role: socio) e `leticia@aldeia.com.br` (role: socio)

**Importante:** Após criar os usuários no Auth, você precisa inserir os dados correspondentes na tabela `users` (via Table Editor), vinculando o `auth_user_id` ao ID gerado pelo Supabase Auth.

---

## Etapa 3 — Conectar o Dashboard ao Supabase (30 min)

Esta etapa requer que eu (Manus) faça a integração no código. O que preciso de você:

**Informações necessárias:**

| Dado | Onde encontrar |
|---|---|
| **Project URL** | Settings > API > Project URL (ex: `https://xxxxx.supabase.co`) |
| **Anon Key** | Settings > API > Project API Keys > `anon` `public` |

**O que eu farei:**

1. Instalar o pacote `@supabase/supabase-js` no projeto
2. Criar o cliente Supabase com as credenciais
3. Substituir os dados simulados por queries reais ao banco
4. Implementar login/logout com Supabase Auth
5. Conectar o RLS para que cada perfil veja apenas seus dados

**Resultado:** Os dashboards passarão a exibir dados reais do banco, e o login controlará automaticamente o que cada usuário vê.

---

## Etapa 4 — Definir a Fonte de Dados (Decisão Estratégica)

A pergunta mais importante para o funcionamento dos dashboards é: **de onde os dados vão vir?**

Existem 3 cenários possíveis:

### Cenário A: Software de gestão com API (Recomendado)

Se vocês escolherem um software como **Feegow**, **Clínica Ágil** ou **SimplesVet** que tenha API, eu posso criar uma integração automática que:
- Puxa os dados de sessões, pacientes e faturamento automaticamente
- Alimenta o Supabase em tempo real (ou a cada hora)
- Elimina entrada manual de dados

**Ação necessária:** Escolher o software de gestão e verificar se ele tem API disponível.

### Cenário B: Entrada manual via formulário

Se o software não tiver API, criaremos formulários no próprio dashboard para:
- Registrar sessões realizadas
- Registrar faturamento diário
- Registrar NPS (via link WhatsApp)

**Prós:** Funciona com qualquer software. **Contras:** Depende de disciplina da equipe.

### Cenário C: Importação via planilha

Exportar dados do software de gestão em CSV/Excel e importar no Supabase periodicamente.

**Prós:** Simples. **Contras:** Não é tempo real, requer trabalho manual semanal.

---

## Etapa 5 — Publicar o Dashboard (10 min)

Quando tudo estiver conectado:

1. Eu faço o build final do projeto
2. Você clica em **Publish** na interface do Manus
3. O dashboard fica acessível via URL (ex: `aldeia-dashboards.manus.space`)
4. Cada colaborador acessa com seu email/senha
5. O RLS garante que cada um vê apenas o que deve ver

**Opcional:** Configurar um domínio personalizado (ex: `painel.aldeiaclinica.com.br`) nas configurações do projeto.

---

## Resumo do Cronograma

| Etapa | Tempo estimado | Quem faz | Dependência |
|---|---|---|---|
| 1. Criar projeto e rodar SQL | 15 min | Rica | Conta Supabase (feito) |
| 2. Configurar autenticação | 20 min | Rica + Manus | Etapa 1 |
| 3. Conectar dashboard ao banco | 30 min | Manus | Etapa 2 + credenciais |
| 4. Definir fonte de dados | Decisão | Rica + Letícia | Software de gestão |
| 5. Publicar | 10 min | Rica | Etapas 1-3 |

**Tempo total estimado:** ~1h30 de trabalho efetivo (sem contar a decisão do software de gestão).

---

## Ação Imediata

A próxima coisa que você precisa fazer agora é:

> **Criar o projeto `aldeia-core` no Supabase e rodar o schema SQL (Etapa 1).** Depois me envie o Project URL e a Anon Key para eu fazer a integração.

Paralelamente, discuta com a Letícia qual software de gestão vocês vão usar — essa decisão impacta diretamente como os dados vão alimentar os dashboards.
