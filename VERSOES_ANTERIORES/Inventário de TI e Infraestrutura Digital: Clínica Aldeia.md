# Inventário de TI e Infraestrutura Digital: Clínica Aldeia

Este documento detalha todos os equipamentos de tecnologia e infraestrutura digital necessários para a operação da Clínica Aldeia. O planejamento foi desenhado considerando a premissa de que **cada terapeuta terá seu próprio computador**, além das necessidades de segurança de dados (LGPD) e da experiência premium que a clínica deseja oferecer.

---

## 1. Equipamentos de Computação (Hardware)

A escolha dos computadores deve focar em durabilidade, velocidade de inicialização (SSDs são obrigatórios) e tamanho compacto para não poluir visualmente as salas de terapia.

### 1.1. Computadores para Terapeutas (Salas de Atendimento)
Como cada terapeuta terá o seu, a máquina precisa ser rápida para preenchimento de prontuários eletrônicos entre as sessões, sem travamentos.
*   **Equipamento Sugerido:** Mini PCs (ex: Dell OptiPlex Micro, Lenovo ThinkCentre Tiny ou Mac Mini) ou Notebooks corporativos leves.
*   **Especificação Mínima:** Processador Intel Core i5 (ou Ryzen 5), 8GB de RAM, 256GB SSD.
*   **Periféricos:** Monitor de 21" a 24" (com ajuste de altura para ergonomia), teclado e mouse sem fio (para evitar fios que as crianças possam puxar).
*   **Quantidade:** 1 por sala de atendimento / por terapeuta.

### 1.2. Computadores para Recepção e Atendimento ao Cliente
A recepção é o centro nervoso da clínica. As máquinas ficam ligadas o dia todo com múltiplas abas abertas (WhatsApp Web, sistema de agendamento, e-mail, planilhas).
*   **Equipamento Sugerido:** Desktop All-in-One (tela e CPU integradas) para um visual clean no balcão, ou Mini PCs escondidos sob a bancada.
*   **Especificação Mínima:** Processador Intel Core i5, 8GB a 16GB de RAM, 256GB SSD.
*   **Quantidade:** 2 unidades (considerando 2 posições de atendimento na recepção para evitar filas).

### 1.3. Computadores para Administração/Diretoria (Backoffice)
Máquinas para o trabalho de Ricardo (Financeiro/Operações) e Letícia (Direção Clínica).
*   **Equipamento Sugerido:** Notebooks corporativos de alta performance (permite mobilidade para reuniões externas ou home office).
*   **Especificação Mínima:** Processador Intel Core i7 (ou Ryzen 7), 16GB de RAM, 512GB SSD.
*   **Quantidade:** 2 unidades.

---

## 2. Infraestrutura de Rede e Conectividade

Uma clínica de saúde não pode ficar sem internet. O sistema de prontuário, agendamento e faturamento será 100% em nuvem.

### 2.1. Roteadores Wi-Fi (Rede Mesh)
O Wi-Fi não pode ter "pontos cegos" nas salas de terapia.
*   **Equipamento Sugerido:** Sistema Wi-Fi Mesh corporativo (ex: TP-Link Deco, Ubiquiti UniFi ou Google Nest Wi-Fi).
*   **Configuração:** É obrigatório criar **duas redes separadas**:
    *   *Rede Aldeia_Corp:* Oculta, apenas para os computadores da clínica (segurança de dados).
    *   *Rede Aldeia_Visitantes:* Aberta para os pais na sala de espera, com limite de banda (para não derrubar a rede principal) e bloqueio de sites impróprios.
*   **Quantidade:** 1 roteador principal + 2 a 3 satélites (dependendo da metragem quadrada da clínica).

### 2.2. Link de Internet Redundante (Backup)
*   **Serviço:** Contratar dois provedores de internet diferentes (ex: Copel Fibra como principal e Claro/Vivo como backup). Se um cair, o roteador (Dual WAN) muda automaticamente para o outro.

---

## 3. Impressão e Digitalização

Apesar do foco no digital, a clínica ainda precisará imprimir contratos, recibos, laudos e materiais terapêuticos (PECS, figuras de comunicação alternativa).

### 3.1. Impressora Multifuncional (Recepção/ADM)
*   **Equipamento Sugerido:** Impressora Laser Monocromática com scanner alimentador automático (ADF).
*   **Justificativa:** Impressão rápida de contratos e digitalização ágil de documentos de pacientes (RG, carteirinha do convênio) direto para o prontuário eletrônico.
*   **Quantidade:** 1 unidade robusta na recepção.

### 3.2. Impressora Colorida (Uso Terapêutico)
*   **Equipamento Sugerido:** Impressora Tanque de Tinta (EcoTank).
*   **Justificativa:** Terapeutas (especialmente Fono e TO) imprimem muitos materiais visuais coloridos para as crianças. A impressora tanque de tinta tem o menor custo por página colorida.
*   **Quantidade:** 1 unidade (pode ficar na sala de materiais/copa dos terapeutas).

---

## 4. Comunicação e Audiovisual

### 4.1. Telefonia (PABX Virtual / VoIP)
Esqueça o PABX físico antigo.
*   **Equipamento Sugerido:** Aparelhos de telefone IP (conectados na rede de internet) ou uso de *Softphones* (aplicativo no computador com headset).
*   **Serviço:** PABX em Nuvem. Permite ter uma URA de atendimento ("Digite 1 para agendamentos, 2 para financeiro"), gravação de chamadas (segurança jurídica) e fila de espera.
*   **Quantidade:** 2 aparelhos IP para a recepção + 1 para o ADM.

### 4.2. TVs para Sala de Espera e Lounge
*   **Equipamento Sugerido:** Smart TVs de 50" a 55".
*   **Justificativa:** Não é para passar TV aberta. As TVs devem rodar conteúdo institucional da Aldeia (vídeos sobre TEA, apresentação da equipe, dicas de Parent Training) ou conteúdo infantil calmante (sem som alto).
*   **Quantidade:** 1 a 2 unidades (dependendo do tamanho da recepção).

### 4.3. Som Ambiente (Opcional, mas recomendado)
*   **Equipamento Sugerido:** Caixas de som embutidas no gesso (recepção e corredores) conectadas a um amplificador Bluetooth.
*   **Justificativa:** Música instrumental em volume muito baixo ajuda a abafar o som das salas de terapia (privacidade) e cria um ambiente acolhedor para os pais.

---

## 5. Equipamentos "Invisíveis" (Mas Críticos)

Estes são os itens que garantem que a clínica não pare de funcionar.

### 5.1. Nobreaks (UPS)
*   **Justificativa:** Em caso de queda de energia, os computadores da recepção e o roteador de internet não podem desligar abruptamente.
*   **Quantidade:** 1 Nobreak para o roteador principal/modem da operadora + 1 Nobreak para cada computador da recepção. (Para os terapeutas, se usarem notebooks, a bateria resolve; se usarem Mini PCs, precisarão de pequenos nobreaks).

### 5.2. Câmeras de Segurança (CFTV)
*   **Equipamento Sugerido:** Câmeras IP com gravação em nuvem ou NVR local.
*   **Localização:** Recepção, corredores, entrada e fachada. **Atenção:** É terminantemente proibido (por questões éticas e de LGPD) colocar câmeras dentro das salas de terapia sem autorização judicial ou consentimento explícito e justificado dos pais.
*   **Quantidade:** 4 a 8 câmeras.

### 5.3. Tablets ou Smartphones (Recepção)
*   **Justificativa:** Para uso exclusivo do WhatsApp Business da clínica. É muito mais ágil ter um aparelho dedicado para isso do que depender apenas do WhatsApp Web no computador da recepção.
*   **Quantidade:** 1 unidade.

---

## Resumo do Checklist de Compras de TI

| Categoria | Item | Quantidade Estimada |
| :--- | :--- | :--- |
| **Computadores** | Mini PCs ou Notebooks (Terapeutas) | 1 por sala |
| **Computadores** | All-in-One ou Mini PCs (Recepção) | 2 |
| **Computadores** | Notebooks Alta Performance (Diretoria/ADM) | 2 |
| **Rede** | Roteadores Wi-Fi Mesh | 1 Kit (3 peças) |
| **Impressão** | Multifuncional Laser (Recepção) | 1 |
| **Impressão** | Impressora Tanque de Tinta Colorida (Terapeutas) | 1 |
| **Comunicação** | Telefones IP (VoIP) | 3 |
| **Comunicação** | Smartphone/Tablet (WhatsApp Clínica) | 1 |
| **Audiovisual** | Smart TV 50" (Recepção) | 1 ou 2 |
| **Segurança** | Nobreaks (Recepção e Roteador) | 3 |
| **Segurança** | Câmeras de CFTV | 4 a 8 |
