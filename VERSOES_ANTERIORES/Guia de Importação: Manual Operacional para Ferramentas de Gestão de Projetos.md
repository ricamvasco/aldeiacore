# Guia de Importação: Manual Operacional para Ferramentas de Gestão de Projetos

Este guia detalha como importar o arquivo `aldeia_controle_tarefas.csv` para ferramentas de gestão de projetos como ClickUp e Asana, transformando o Manual Operacional em um plano de ação gerenciável.

## 1. Entendendo o Arquivo CSV (`aldeia_controle_tarefas.csv`)

O arquivo CSV gerado contém as seguintes colunas, que correspondem aos campos que você encontrará na maioria das ferramentas de gestão de projetos:

*   **Frente:** Categoria principal da tarefa (ex: Jurídico e Regulatório, Marketing).
*   **Fase:** Sub-categoria ou etapa dentro da frente (ex: Fase 1 — Formalização da Empresa).
*   **Sub-tarefa:** O nome da tarefa específica a ser realizada (ex: Definição da Natureza Jurídica).
*   **Detalhamento:** Uma descrição mais completa da tarefa.
*   **Entregável:** O resultado esperado da tarefa.
*   **Responsável:** A pessoa ou equipe designada para a tarefa.
*   **Prazo:** A data limite para a conclusão da tarefa (formato AAAA-MM-DD).
*   **Fatores Críticos de Sucesso:** Observações importantes para o êxito da tarefa.

## 2. Guia de Importação Geral (Aplicável a ClickUp, Asana e Outros)

A maioria das ferramentas de gestão de projetos segue um processo de importação similar. As etapas gerais são:

1.  **Acesse a Ferramenta de Gestão de Projetos:** Faça login na sua conta (ClickUp, Asana, etc.).
2.  **Localize a Opção de Importação:** Geralmente, a opção de importação está em `Configurações`, `Espaço de Trabalho`, `Projetos` ou `Listas`. Procure por termos como `Importar`, `Importar CSV`, `Importar Dados`.
3.  **Selecione o Arquivo CSV:** Escolha o arquivo `aldeia_controle_tarefas.csv` do seu computador.
4.  **Mapeie as Colunas:** Esta é a etapa mais importante. A ferramenta pedirá para você "mapear" as colunas do seu CSV para os campos existentes na ferramenta. Por exemplo:
    *   `Sub-tarefa` do CSV deve ser mapeado para `Nome da Tarefa` ou `Título da Tarefa`.
    *   `Detalhamento` do CSV pode ser mapeado para `Descrição`.
    *   `Responsável` do CSV deve ser mapeado para `Atribuído a` ou `Responsável`.
    *   `Prazo` do CSV deve ser mapeado para `Data de Vencimento` ou `Prazo Final`.
    *   `Frente` e `Fase` podem ser mapeados para `Pastas`, `Listas`, `Projetos`, `Tags` ou `Campos Personalizados` (Custom Fields), dependendo da estrutura que você deseja criar na ferramenta.
    *   `Entregável` e `Fatores Críticos de Sucesso` podem ser mapeados para `Descrição` (se houver espaço) ou `Campos Personalizados`.
5.  **Configure Opções Adicionais:** Algumas ferramentas permitem definir o status padrão das tarefas importadas (ex: `A Fazer`, `Pendente`), ou se deseja criar novas tags/campos personalizados automaticamente.
6.  **Inicie a Importação:** Confirme as configurações e inicie o processo. A ferramenta processará o arquivo e criará as tarefas.

## 3. Dicas Específicas para ClickUp e Asana

### ClickUp

*   **Estrutura:** No ClickUp, você pode usar `Espaços` para as Frentes, `Pastas` para as Fases e `Listas` para organizar as sub-tarefas. Alternativamente, `Frente` e `Fase` podem ser `Campos Personalizados` do tipo `Dropdown`.
*   **Importação:** Vá para o `Espaço` ou `Pasta` onde deseja importar. Clique em `+ Tarefa` (ou `+ Novo`) e procure por `Importar`. Selecione `CSV` e siga as instruções de mapeamento.
*   **Campos Personalizados:** Se você mapear `Frente`, `Fase`, `Entregável` e `Fatores Críticos de Sucesso` para campos personalizados, certifique-se de criá-los antes da importação para que o mapeamento seja mais preciso.

### Asana

*   **Estrutura:** No Asana, você pode criar `Projetos` para as Frentes, `Seções` para as Fases e as `Tarefas` para as sub-tarefas. `Entregável` e `Fatores Críticos de Sucesso` podem ser adicionados na `Descrição` da tarefa ou como `Campos Personalizados`.
*   **Importação:** Abra o `Projeto` onde deseja importar. Clique no botão `+` (Adicionar) e selecione `Importar`. Escolha `CSV` e siga o assistente de mapeamento.
*   **Colaboradores:** Certifique-se de que os nomes dos responsáveis no seu CSV correspondam exatamente aos nomes dos usuários no Asana para que as tarefas sejam atribuídas corretamente.

## 4. Recomendações Finais

*   **Teste com um Subconjunto:** Antes de importar o arquivo completo, tente importar apenas as primeiras 5-10 linhas para verificar se o mapeamento das colunas está correto e se as tarefas são criadas conforme o esperado.
*   **Limpeza de Dados:** Revise o CSV antes da importação para corrigir quaisquer erros de digitação ou inconsistências, especialmente nos nomes dos responsáveis e nas datas.
*   **Comunicação:** Após a importação, comunique à sua equipe que as tarefas foram adicionadas e oriente-os sobre como acessá-las e utilizá-las na ferramenta escolhida.

Com este arquivo CSV e o guia, você terá um controle robusto sobre todas as tarefas necessárias para a inauguração da Aldeia Clínica. Caso tenha dúvidas durante o processo de importação, consulte a documentação da ferramenta escolhida ou o suporte técnico deles.
