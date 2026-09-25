# Entrega 1 — Modelo Conceitual (DER)
### Modelagem de um sistema de gestão de informações para uma organização de pequeno porte

---

## Metadados

- **Nomes dos alunos e RGM:**
  - Erick da Silva Elias, RGM: 47676779
  - Fabricio Coutinho, RGM: 4795228  
  - Marcella Flandes Souza De Mello, RGM: 48386278
  - Matheus Mendes Fagundes, RGM: 48296457
  - Henry Amaral Pires, RGM: 49937707

---

## 1. Caracterização da Organização

- **Nome e natureza da organização:** JV industria, empresa fabricante de materiais para construção civil (argamassas, texturas e afins), que produz sob encomenda conforme pedido do cliente.  

- **Contexto e porte:** Empresa de pequeno/médio porte, com fins lucrativos.  — número aproximado de funcionários envolvidos na operação: recepção/conferência, estoque, separação, expedição, motoristas, administrativo.  (escrever) volume aproximado de atividades observado: nº de pedidos processados por dia/semana, nº de entregas, nº de fornecedores atendidos, nº de clientes ativos

- **Problemas e necessidades identificados:**



- **Justificativa da escolha:** PREENCHER — por que essa organização foi escolhida (acesso garantido).

- **Evidências da organização:**
  - Endereço completo:  Av. Ademar Pereira de Barros, 876 - Jardim Santa Maria, Jacareí - SP
  - Contato: adm2@jvindustria.com.br/ (12) 3958-3431
  - e nome do responsável entrevistado
  - Site: https://jvindustria.com.br/
  - Fotos da visita (anexar no repositório)

---

## 2. Processos de Negócio  (FIZ)

- **Principais processos mapeados:**
  - **Recebimento de pedidos:** o cliente informa o produto desejado e a quantidade (em kg) necessária.  
  - **Emissão de fórmula:** com base no pedido, é emitida no sistema a fórmula de produção do produto solicitado.
  - **Separação de matérias-primas:** os insumos necessários para a fórmula são separados no setor correspondente.
  - **Direcionamento para a máquina:** cada máquina é dedicada a um tipo específico de produto; a fórmula é enviada para a máquina correta.
  - **Fabricação do produto:** a máquina realiza a produção conforme a fórmula emitida.
  - **Registro da produção:** ao final da fabricação, a quantidade produzida é lançada no sistema e a fórmula é encerrada.
  - **Expedição:** o produto fabricado é levado para o setor de expedição, que registra a entrada da quantidade em estoque.
  - **Emissão de nota fiscal e contratação de entrega:** após a confirmação da expedição, é emitida a nota fiscal e contratado o veículo responsável pela entrega ao cliente.


- **Fluxogramas:**
  
---

## 3. Requisitos do Sistema

### 3.1 Requisitos Funcionais

- O sistema deve permitir cadastrar, consultar, editar e inativar clientes.
- O sistema deve permitir cadastrar produtos (massa corrida, rejunte, massa acrílica, texturas, grafiato, cimento queimado, massa para drywall, impermeabilizante, etc.).
- O sistema deve permitir registrar um pedido de cliente, informando o produto e a quantidade solicitada (em kg).
- O sistema deve permitir emitir uma fórmula de produção a partir de um pedido, vinculando o produto e a quantidade planejada.
- O sistema deve permitir registrar as matérias-primas necessárias para cada fórmula e a quantidade de cada uma.
- O sistema deve permitir associar uma fórmula à máquina correspondente ao tipo de produto a ser fabricado.
- O sistema deve permitir registrar a quantidade efetivamente produzida ao final da fabricação e encerrar a fórmula correspondente.
- O sistema deve permitir registrar a entrada de produtos acabados no estoque após a expedição.
- O sistema deve permitir emitir a nota fiscal vinculada a um pedido, após a confirmação da expedição.
- O sistema deve permitir registrar a entrega, associando o veículo contratado ao pedido e à nota fiscal.
- O sistema deve permitir consultar o status de um pedido ao longo de todo o processo (recebido, em fórmula, em produção, expedido, faturado, entregue).
- O sistema deve permitir consultar a quantidade de cada matéria-prima e produto disponível em estoque.

### 3.2 Requisitos Não Funcionais

- **Desempenho:** o sistema deve responder às consultas de estoque de matéria-prima em tempo hábil para não atrasar a separação e o início da produção.
- **Disponibilidade:** o sistema deve estar disponível durante o horário de funcionamento da fábrica.
- **Segurança:** o acesso a dados de clientes, valores de pedidos e notas fiscais deve ser restrito a usuários autorizados (administrativo/financeiro).
- **Usabilidade:** a interface usada no chão de fábrica (registro de fórmula, encerramento de produção) deve ser simples o suficiente para operadores de máquina sem formação técnica em TI.
- **Integridade:** o sistema não deve permitir o encerramento de uma fórmula sem o registro da quantidade efetivamente produzida.
- **Rastreabilidade:** o sistema deve manter o histórico de cada lote produzido, vinculado à fórmula, à máquina e ao pedido de origem.

---

## 4. Regras de Negócio

- **Regras operacionais:**
  - A quantidade produzida de cada produto é determinada exclusivamente pelo pedido do cliente (em kg); não há produção especulativa sem pedido associado.
  - Cada produto possui uma fórmula própria e fixa, que não muda entre um pedido e outro.
  - Cada fórmula emitida no sistema corresponde a um único produto e uma única quantidade planejada, definidos a partir do pedido do cliente.
  - Cada máquina é dedicada exclusivamente a um tipo de produto; após a mistura na batedora, o material é direcionado à máquina correspondente ao produto solicitado.
  - Uma fórmula só é encerrada no sistema após o registro da quantidade efetivamente produzida.
  - Toda produção recebe número de produção, lote, data de fabricação e validade do produto, garantindo rastreabilidade.
  - A entrada de produto em estoque ocorre automaticamente no sistema assim que a fórmula é baixada ao final da produção, e é confirmada/registrada novamente pela expedição ao receber os produtos.
  - O estoque disponível pode ser consultado pelo código do produto, e também é exibido automaticamente no momento da emissão da nota fiscal.
  - A nota fiscal só é emitida após a expedição registrar a entrada dos produtos.
  - A contratação do veículo de entrega ocorre após a emissão da nota fiscal.
  - O pedido possui status "Orçamento" enquanto está em produção, e passa a "Pedido Faturado" quando o cliente realiza a retirada.
  - O pedido pode ser alterado a qualquer momento antes do início da produção.
  - O pedido pode ser cancelado, desde que o cliente avise com antecedência e a produção ainda não tenha sido iniciada.
  - Pedidos destinados a faturamento exigem que o cliente esteja com o nome limpo (sem restrições cadastrais) e respeitem um valor mínimo de R$ 800,00.
  - Pedidos pagos à vista com retirada no local não possuem restrição de valor mínimo nem exigência de nome limpo.

- **Restrições organizacionais:**
  - A concessão de faturamento (venda a prazo) está condicionada à situação cadastral do cliente (ausência de restrições) e a um valor mínimo de pedido, prática comum no setor para mitigar risco de inadimplência.
  - O cancelamento de pedidos é limitado ao período anterior ao início da produção, já que os materiais são fabricados sob encomenda e o cancelamento após o início geraria perda de matéria-prima e tempo de máquina.
  - A rastreabilidade obrigatória por lote/validade/data de fabricação provavelmente atende a normas técnicas do setor de construção civil (garantia de qualidade dos materiais).

---

## 5. Dicionário de Dados Conceitual 

---

## 6. Modelagem Conceitual (Entidades, Atributos, Relacionamentos)

- **Entidades reconhecidas:** Cliente, Fornecedor, Produto, Estoque, Pedido, Item_Pedido, Entrega, Veículo, Funcionário.

- **Atributos e classificações:** 

- **Relacionamentos pertinentes:**
  - Cliente **realiza** Pedido (1:N)
  - Pedido **contém** Item_Pedido (1:N)
  - Produto **compõe** Item_Pedido (1:N)
  - Fornecedor **fornece** Produto (1:N)
  - Produto **é armazenado em** Estoque (1:N)
  - Pedido **gera** Entrega (1:1, opcional)
  - Veículo **realiza** Entrega (1:N)
  - Funcionário **conduz** Veículo (1:N)

- **Restrições e políticas organizacionais aplicadas ao modelo:** [PREENCHER — relacione as regras de negócio da Seção 4 com as restrições de cardinalidade/obrigatoriedade do modelo]

---

## 7. Diagrama Entidade-Relacionamento (DER)

---

## 8. Justificativa Técnica

PREENCHER — Explique e defenda as decisões de abstração tomadas: por que essas entidades específicas (e não outras), por que esses atributos, por que essas cardinalidades. Por exemplo: por que Entrega foi modelada como entidade separada de Pedido em vez de atributos do próprio pedido; por que Item_Pedido existe como entidade associativa em vez de relacionamento direto N:N entre Pedido e Produto; por que Estoque foi separado de Produto (permite múltiplas localizações por produto).

---

## 9. Uso de Inteligência Artificial

| Item | Registro |
|------|------------------|
| **Ferramenta e etapa** | Claude (Anthropic) — utilizado ao longo de toda a Entrega 1: estruturação do modelo conceitual, elaboração de um diagrama ER inicial de exemplo, organização do README a partir do esqueleto da disciplina, revisão de seções específicas (Processos de Negócio, Requisitos do Sistema, Regras de Negócio, Modelagem Conceitual, Justificativa Técnica) e orientação técnica sobre uso do GitHub (criação de repositório, permissões de colaborador, formatação Markdown, anexação de imagens). |
| **Motivação** | O grupo recorreu à IA para ter um ponto de partida estruturado do README, entender a notação de modelagem ER/DER (BR e Crow's Foot), esclarecer dúvidas práticas sobre uso do GitHub (Markdown, colaboradores, upload de arquivos) e receber apoio na redação técnica de seções como a Justificativa Técnica. |
| **Prompt(s) utilizados** | "preciso criar um banco de dados sobre uma empresa escolhida, que foi um centro logístico, e antes, preciso fazer um diagrama no br modelo ou db design, como posso fazer?"; "baseado no que eu disse, preciso criar um readme.md"; "consegue preencher cada área com informações fictícias de uma empresa fictícia para eu ver como deve ficar?"; "eu preciso criar esse arquivo no github, e como o trabalho é em grupo, me indicaram fazer diretamente por ele..."; "Produtos: massa corrida / Rejunte / Massa acrílica... [descrição do processo produtivo real]"; "na seção 2, como que fica os simbolos"; "na seção 4?"; "na seção 3 (Requisitos do sistema) oque exatamente devo escrever?"; entre outros prompts de dúvidas pontuais sobre formatação e uso do GitHub. |
| **Resposta recebida** | A IA gerou uma estrutura completa de README.md alinhada ao esqueleto da disciplina, um exemplo ilustrativo com uma empresa fictícia (posteriormente identificado como inadequado, pois o enunciado exige organização real), orientações passo a passo sobre GitHub (criação de repositório, adição de colaboradores, upload de arquivos e imagens), e sugestões de conteúdo para as seções de Processos de Negócio, Requisitos Funcionais/Não Funcionais, Regras de Negócio e Justificativa Técnica, adaptadas à operação real da empresa a partir das informações fornecidas pelo grupo. |
| **Fontes consultadas e verificadas** | A IA não citou fontes externas nas respostas técnicas de modelagem; o conteúdo foi baseado em conhecimento geral de modelagem de dados (ER/DER, notação BR, Markdown, GitHub). Todo o conteúdo específico da empresa (processos, produtos, fluxo de produção) foi validado pelo grupo com base na visita de campo realizada, não em informações fornecidas pela IA. |
| **Trechos rejeitados ou corrigidos** | O grupo rejeitou integralmente o primeiro modelo sugerido pela IA (baseado em uma empresa fictícia genérica de distribuição/centro logístico, com entidades como Fornecedor, Item_Pedido, Veículo padrão), substituindo por um modelo específico da operação real da JV Indústria, que envolve fabricação sob encomenda (entidades como Formula, Matéria_Prima, Máquina, Lote, Produção). O Dicionário de Dados e o DER final foram construídos pelo grupo com base no processo real, não no exemplo genérico inicial. |
| **Justificativa da escolha final** | O grupo optou por manter a estrutura geral de organização do README sugerida pela IA (por seguir fielmente o esqueleto da disciplina), mas substituiu todo o conteúdo específico — entidades, atributos, relacionamentos, regras de negócio e justificativa técnica — pelas informações reais levantadas na visita à empresa, garantindo que o trabalho reflita a operação observada e não um modelo genérico. |
| **Reflexão crítica** | A IA inicialmente sugeriu, sem que o grupo tivesse explicitado a exigência do enunciado, uma modelagem para uma empresa totalmente fictícia — o que não atende ao requisito de organização real e pesquisada em campo. Esse ponto só foi corrigido porque a própria IA identificou a inconsistência ao ler o esqueleto da entrega e alertou o grupo, reforçando a importância de revisar cuidadosamente as instruções da disciplina antes de aceitar sugestões de IA. Além disso, a IA não teve acesso direto ao board do Figma nem ao repositório do GitHub (por restrições de acesso automatizado), então parte da leitura de diagramas foi feita a partir de prints de tela, o que pode ter gerado pequenas imprecisões na transcrição de cardinalidades — exigindo conferência manual do grupo contra o diagrama original. |

---

**Uso adicional (integrante responsável pela entrevista de campo):**

| Item | Registro |
|------|------------------|
| **Ferramenta e etapa** | ChatGPT (OpenAI) — organização do levantamento bruto de informações coletado na entrevista de campo (transcrição de falas do responsável entrevistado) em categorias (Entidades, Processos, Dados/Regras), com referência de origem de cada trecho. |
| **Motivação** | O levantamento de campo foi registrado de forma corrida/desestruturada (mensagens de texto); o grupo recorreu à IA para organizar esse material bruto em categorias úteis à modelagem, sem perder nenhuma informação relatada. |
| **Prompt(s) utilizados** | "Vou te enviar várias mensagens. Quero que você organize todo esse conteúdo de forma clara e estruturada... Organize por categorias: Entidades, Processos e Dados/Outras informações... Indique a referência de qual mensagem veio cada informação" (seguido da transcrição bruta da entrevista). |
| **Resposta recebida** | Documento estruturado com o levantamento organizado em Entidades, Processos, Dados/Regras de Negócio (numeradas RN01–RN26) e um fluxo geral da produção, cada trecho referenciado à fala original do entrevistado. |
| **Fontes consultadas e verificadas** | Nenhuma fonte externa; a IA apenas reorganizou informações fornecidas diretamente pelo grupo a partir da entrevista de campo, sem adicionar conteúdo próprio. |
| **Trechos rejeitados ou corrigidos** | [PREENCHER pelo integrante que usou — ex.: alguma categorização foi reagrupada manualmente, alguma regra duplicada foi consolidada] |
| **Justificativa da escolha final** | A organização por categorias (Entidades/Processos/Regras) facilitou a transição direta desse levantamento para o MER e o dicionário de dados, mantendo rastreabilidade da fala original de onde cada regra foi extraída. |
| **Reflexão crítica** | Como a IA apenas reorganiza e não valida o conteúdo, cabe ao grupo confirmar que nenhuma informação foi mal interpretada na reorganização — por exemplo, distinguir corretamente entre regras aplicáveis a "faturamento" e a "retirada com pagamento à vista", que têm condições diferentes. |

---

