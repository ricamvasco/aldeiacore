# Brainstorm de Design — Aldeia Dashboards

## Contexto
Protótipo de 3 telas de dashboard para a Clínica Aldeia (TEA/neurodesenvolvimento):
- **Tela 1:** Visão Sócio (executiva) — Rica e Letícia
- **Tela 2:** Visão Líder de Área (tática) — Líderes de Fonoaudiologia, Psicologia, etc.
- **Tela 3:** Visão Terapeuta (operacional) — KPIs individuais e jornada de carreira

Cores da Aldeia: Verde (#2E7D32), Bege/Off-white (#F5F0E8), Marrom terra (#5D4037), Laranja acolhedor (#E65100).

---

<response>
<text>
## Ideia 1: "Floresta de Dados" — Biophilic Data Visualization

**Design Movement:** Biophilic Design aplicado a interfaces digitais. Inspirado em painéis de controle de estufas e jardins botânicos inteligentes.

**Core Principles:**
1. Dados como organismos vivos — cada KPI é representado como um elemento orgânico que "cresce" conforme o desempenho
2. Hierarquia por densidade vegetal — mais verde = mais saudável
3. Navegação por "camadas de solo" — cada nível de profundidade revela mais detalhe

**Color Philosophy:** Verde musgo (#2E7D32) como cor de saúde/sucesso, marrom terra (#5D4037) como base/fundação, bege linho (#F5F0E8) como espaço respirável, laranja (#E65100) apenas para alertas críticos. O fundo é um off-white quente que simula papel kraft.

**Layout Paradigm:** Dashboard com sidebar fixa à esquerda (navegação entre as 3 visões) e área principal dividida em "canteiros" — blocos orgânicos com bordas suaves que lembram parcelas de terra. Gráficos usam formas orgânicas (area charts com curvas suaves, não barras rígidas).

**Signature Elements:**
1. Ícone de árvore da Aldeia como avatar do sistema — a árvore "cresce" conforme os KPIs melhoram
2. Indicadores de nível de carreira representados como estágios de crescimento (semente → árvore) com ilustrações botânicas minimalistas
3. Gauge charts circulares que lembram anéis de crescimento de troncos de árvore

**Interaction Philosophy:** Hover revela "raízes" — detalhes ocultos que sustentam o número principal. Transições suaves como brisa.

**Animation:** Entrada de dados com efeito de "brotamento" — números crescem do zero como plantas emergindo. Gráficos se desenham da esquerda para a direita como raízes se espalhando.

**Typography System:** DM Sans (headings, bold 700) + Inter (body, regular 400). Números grandes em DM Sans Bold para impacto.
</text>
<probability>0.07</probability>
</response>

<response>
<text>
## Ideia 2: "Painel Clínico" — Swiss Healthcare Dashboard

**Design Movement:** Swiss International Style adaptado para healthcare analytics. Inspirado em painéis de monitoramento hospitalar de alta precisão.

**Core Principles:**
1. Precisão cirúrgica na apresentação de dados — cada pixel tem propósito
2. Código de cores semafórico integrado à paleta da Aldeia
3. Densidade informacional alta com legibilidade perfeita

**Color Philosophy:** Fundo branco puro (#FFFFFF) com grid sutil cinza (#F0F0F0). Verde Aldeia (#2E7D32) para métricas positivas/on-target. Marrom (#5D4037) para textos e labels. Laranja (#E65100) para warning. Vermelho (#C62828) para critical. A paleta é funcional, não decorativa.

**Layout Paradigm:** Grid rígido de 12 colunas. Header fixo com tabs para alternar entre as 3 visões. KPIs em cards horizontais no topo (stat cards). Gráficos em grid 2x2 abaixo. Tabela de dados na parte inferior. Zero decoração — apenas dados.

**Signature Elements:**
1. Stat cards com micro-sparklines inline (tendência dos últimos 30 dias ao lado do número)
2. Barra de progresso vertical para o nível de carreira do terapeuta (como um termômetro clínico)
3. Badge system com cores semafóricas para status de cada KPI

**Interaction Philosophy:** Click-to-drill-down. Cada número é clicável e revela a query/detalhe por trás dele. Sem surpresas, sem animações desnecessárias.

**Animation:** Apenas transições de fade entre telas (200ms). Números fazem count-up ao carregar. Nada mais.

**Typography System:** Space Grotesk (headings e números, monospaced feel) + Work Sans (body text). Números em Space Grotesk Medium para alinhamento perfeito em tabelas.
</text>
<probability>0.05</probability>
</response>

<response>
<text>
## Ideia 3: "Terra Fértil" — Warm Brutalist Dashboard

**Design Movement:** Warm Brutalism — a honestidade estrutural do brutalismo suavizada com a paleta terrosa da Aldeia. Inspirado em dashboards de startups de impacto social.

**Core Principles:**
1. Blocos de conteúdo com bordas grossas e sombras duras — cada seção é um "tijolo" do dashboard
2. Tipografia oversized para números-chave — os dados gritam, não sussurram
3. Contraste máximo entre fundo e conteúdo

**Color Philosophy:** Fundo bege cru (#F5F0E8) como argila. Blocos com fundo branco e borda grossa marrom (#5D4037, 3px). Verde (#2E7D32) para fills de gráficos e badges de sucesso. Laranja (#E65100) para CTAs e destaques urgentes. Sombras duras (4px offset, sem blur) em marrom.

**Layout Paradigm:** Layout assimétrico com blocos de tamanhos variados. O KPI mais importante ocupa 50% da largura. Sidebar colapsável com ícones grandes. Gráficos de barra com cantos retos e cores sólidas (sem gradientes). Tabelas com linhas zebradas em bege.

**Signature Elements:**
1. Números de KPI em tamanho 72px com fonte bold — impossível ignorar
2. Bordas duplas nos cards mais importantes (como molduras de quadro)
3. Ícones da jornada Aldeia (semente→árvore) desenhados em estilo lineart grosso

**Interaction Philosophy:** Hover adiciona uma segunda sombra (efeito de "levantar o bloco"). Clicks são confirmados com micro-bounce. Feedback tátil e direto.

**Animation:** Blocos entram com slide-up escalonado (stagger 50ms). Números fazem count-up rápido (400ms). Gráficos se preenchem de baixo para cima como terra sendo depositada.

**Typography System:** Space Grotesk Bold (headings e números grandes) + DM Sans Regular (body e labels). Contraste extremo entre tamanhos: H1 = 72px, body = 14px.
</text>
<probability>0.04</probability>
</response>

---

## Decisão: Ideia 1 — "Floresta de Dados" (Biophilic Data Visualization)

Escolho a Ideia 1 porque é a que melhor conversa com a identidade da Aldeia (árvore, crescimento, natureza) e cria uma experiência visual única que os terapeutas vão se identificar. O conceito de "crescimento" permeia tanto os KPIs quanto a jornada de carreira, criando coerência entre dados e narrativa.
