# Entrega 1 — Modelo Conceitual (DER)
### Modelagem de um sistema de gestão de informações para uma organização de pequeno porte

---

## Metadados

| **Nomes** | **RGM** |
|---|---|
| [Erick da Silva Elias](https://github.com/erickdasilvaelias) | 47676779 |
| [Fabricio Coutinho](https://github.com/Briciobio) | 4795228 |
| [Henry Amaral Pires](https://github.com/HenryPires505) | 49937707
| [Marcella Flandes Souza De Mello](https://github.com/marcellaflandes) | 48386278 |
| [Matheus Mendes Fagundes](https://github.com/Matheus-212) | 48296457 |

## 1. Caracterização da Organização

- **Nome e natureza da organização:** JV Indústria, empresa fabricante de materiais para construção civil (argamassas, texturas e afins), que produz sob encomenda conforme pedido do cliente.

- **Contexto e porte:** Empresa de pequeno/médio porte, com fins lucrativos, totalizando 30 funcionários diretos, distribuídos da seguinte forma: 19 na produção, 4 no administrativo, 3 no laboratório, 2 na expedição e 2 no estoque de embalagens. A empresa realiza em média 25 cargas de entrega por semana.

- **Problemas e necessidades identificados:** Um dos principais pontos de atenção na operação é a eventual quebra de máquinas durante a produção — a empresa mantém uma equipe de manutenção terceirizada atuando dentro da própria fábrica para resolver essas paradas rapidamente, o que indica a importância de rastrear, no sistema, o histórico de produção por máquina e eventuais interrupções, já que isso impacta diretamente o cumprimento dos pedidos.

 - **Justificativa da escolha:** A JV Indústria foi escolhida porque um dos integrantes do grupo possui vínculo familiar, o que garantiu acesso facilitado para a realização da visita presencial e da entrevista com a responsável. Esse acesso direto foi decisivo para viabilizar um levantamento de requisitos real e aprofundado, conforme exigido pela disciplina. Além disso, o porte e a complexidade dos processos observados (produção sob encomenda, controle de fórmulas, estoque e expedição) se mostraram adequados ao escopo desta primeira etapa do trabalho.

- **Evidências da organização:**
  - Endereço completo:  Av. Ademar Pereira de Barros, 876 - Jardim Santa Maria, Jacareí - SP
  - Contato: adm2@jvindustria.com.br/ (12) 3958-3431
  - Entrevistado: Eliane Silveira do Carmo
  - Site: https://jvindustria.com.br/
  - Fotos da visita (anexar no repositório)

---

## 2. Processos de Negócio

- **Principais processos mapeados:**
  - **Recebimento de pedidos:** o cliente informa o produto desejado e a quantidade (em kg) necessária.
  - **Emissão de fórmula:** com base no pedido, é emitida no sistema a fórmula de produção do produto solicitado.
  - **Separação de matérias-primas:** os insumos necessários para a fórmula são separados no setor correspondente.
  - **Direcionamento para a máquina:** cada máquina é dedicada a um tipo específico de produto; a fórmula é enviada para a máquina correta.
  - **Fabricação do produto:** a máquina realiza a produção conforme a fórmula emitida.
  - **Registro da produção:** ao final da fabricação, a quantidade produzida é lançada no sistema e a fórmula é encerrada.
  - **Expedição:** o produto fabricado é levado para o setor de expedição, que registra a entrada da quantidade em estoque.
  - **Emissão de nota fiscal e contratação de entrega:** após a confirmação da expedição, é emitida a nota fiscal e contratado o veículo responsável pela entrega ao cliente.


- **Fluxograma:**<br>
<p align="center"><img src="img/fluxograma.jpg" width="400px"></img></p>

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

| Entidade | Relaciona-se com | Cardinalidade |
|---|---|---|
| Cliente | Pedido | 0.N — Um cliente pode possuir ou não N pedidos, todo pedido pertence a um único cliente. |
| Pedido | Nota Fiscal | 1.1 — Um pedido gera apenas uma nota fiscal, e cada nota fiscal está vinculada a exatamente um pedido. |
| Pedido | Item_pedido | 1.N — Um pedido deve conter pelo menos um ou vários itens, e cada item pedido pertence a um único pedido. |
| Item_pedido | Produto | 1.1 — Cada item do pedido refere-se obrigatoriamente a exatamente um produto cadastrado. |
| Produto | Item_pedido | 0.N — Um produto pode nunca ter sido vendido ou estar presente em múltiplos itens de pedidos. |
| Produto | Estoque | 0.N — Um produto pode possuir nenhum ou vários registros de controle de localização em estoque. |
| Estoque | Movimento no Estoque | 0.N — Um registro de estoque pode sofrer nenhuma ou múltiplas movimentações ao longo do tempo. |
| Produto | Fórmula | 1.1 — Um produto possui obrigatoriamente uma única fórmula para a sua fabricação. |
| Fórmula | Matéria Prima | 1.N — Uma fórmula utiliza obrigatoriamente uma ou várias matérias-primas em sua composição. |
| Matéria Prima | Máquina | 0.N — Uma matéria-prima pode ser processada por nenhuma ou várias máquinas na fábrica. |
| Máquina | Lote | 0.N — Uma máquina pode fabricar nenhum ou vários lotes de produtos. |
| Lote | Produto | 1.1 — Todo lote fabricado contém obrigatoriamente um único tipo de produto. |
| Pedido | Entrega | 1.1 — Um pedido está associado a exatamente uma entrega, e cada entrega atende a um pedido. |
| Entrega | Veículos | 1.1 — Uma entrega utiliza obrigatoriamente um único veículo para o transporte. |



## 6. Modelagem Conceitual (Entidades, Atributos, Relacionamentos)

- **Entidades reconhecidas:** Cliente, Pedido, Item_Pedido, Produto, Formula, Matéria_Prima, Fornecedores, Máquina, Produção, Lote, Estoque, Expedição, Nota_Fiscal, Veículo. Cada entidade corresponde a uma etapa ou elemento concreto identificado no processo real da empresa: desde o pedido do cliente até a entrega final, passando pela emissão da fórmula, consumo de matéria-prima, fabricação em máquina dedicada, controle de lote e expedição.

- **Relacionamentos pertinentes:**
  - Cliente **realiza** Pedido (0,N) : (1,1) — Um cliente pode realizar nenhum ou vários pedidos, mas cada pedido pertence a um único cliente.
  - Pedido **possui** Item_Pedido (1,1) : (1,N) — Um pedido deve possuir pelo menos um ou vários itens, e cada item pertence a exatamente um pedido.
  - Item_Pedido **refere-se** Produto (1,1) : (1,1) — Cada item do pedido refere-se obrigatoriamente a exatamente um produto.
  - Formula **define** Produto (1,1) : (1,1) — Reflete a regra de que cada produto tem uma fórmula própria e fixa.
  - Formula **utiliza** Matéria_Prima (1,1) : (1,N) — Uma fórmula utiliza obrigatoriamente uma ou várias matérias-primas.
  - Matéria_Prima **abastece** Máquina (1,N) : (1,N) — Uma matéria-prima pode abastecer várias máquinas e uma máquina pode ser abastecida por várias matérias-primas.
  - Fornecedores **fornece** Matéria_Prima (1,1) : (1,N) — Um fornecedor pode fornecer várias matérias-primas, e cada matéria-prima é fornecida por um fornecedor específico.
  - Produto **origina** Produção (1,1) : (1,N) — Um produto pode originar várias produções, e cada ordem de produção gera um produto específico.
  - Produção **gera** Lote (1,N) : (1,1) — Uma produção pode gerar um ou vários lotes, e cada lote pertence a uma única produção.
  - Lote **está em** Estoque (1,1) : (0,N) — Um lote está armazenado em um estoque específico, e o estoque pode conter nenhum ou vários lotes.
  - Pedido **gera** Expedição (1,1) : (1,N) — Um pedido gera uma ou mais etapas de expedição para entrega.
  - Expedição **emite** Nota_Fiscal (1,1) : (1,1) — Cada expedição emite exatamente uma nota fiscal correspondente.
  - Expedição **emite** Veículo (1,N) : (0,N) — Uma expedição vincula um ou mais veículos, enquanto um veículo pode participar de nenhuma ou várias expedições.

- **Restrições e políticas organizacionais aplicadas ao modelo:**
  - A obrigatoriedade de Formula estar sempre vinculada a um único Produto (1,1) reflete a regra de que cada produto possui fórmula própria e fixa, que não muda entre pedidos.
  - A cardinalidade entre Matéria_Prima e Máquina (via "abastece") busca refletir a regra de que cada máquina é dedicada a um tipo específico de produto, consumindo matérias-primas específicas.
  - A obrigatoriedade de Produção gerar Lote (1,1) reflete a regra de que toda produção recebe número, lote, validade e data de fabricação, garantindo rastreabilidade.
  - A sequência Expedição → Nota_Fiscal → Veículo reflete a regra de que a nota fiscal só é emitida após a expedição confirmar o recebimento, e o veículo só é contratado depois da nota fiscal.


## 7. Diagrama Entidade-Relacionamento (DER)

![DER - JV Indústria](img/der.jpg)

O diagrama acima representa as entidades, atributos, relacionamentos e cardinalidades levantados a partir do processo produtivo da JV Indústria, cobrindo desde o recebimento do pedido do cliente até a entrega final — passando pela emissão de fórmula, consumo de matéria-prima, fabricação em máquina dedicada, controle de lote, entrada em estoque, expedição e faturamento.

**Entidades representadas:** Cliente, Pedido, Item_pedido, Produto, Formula, Matéria_prima, Fornecedores, Máquina, Produção, Lote, Estoque, Expedição, Nota_fiscal, Veículo.

---

## 8. Justificativa Técnica

A entidade **Item_pedido** foi modelada como entidade associativa entre Pedido e Produto, em vez de um relacionamento direto N:N, porque cada item de um pedido carrega informações próprias (quantidade solicitada, por exemplo) que não pertencem exclusivamente nem ao Pedido nem ao Produto isoladamente. Essa decisão também reflete a realidade observada: um mesmo pedido pode conter múltiplos produtos, e um mesmo produto pode aparecer em múltiplos pedidos diferentes.

A entidade **Formula** foi separada de Produto porque, apesar de cada produto possuir uma fórmula própria e fixa (conforme relatado na entrevista), a fórmula representa um processo com atributos e ciclo de vida próprios — status, versão, data de emissão — que não fazem sentido como atributos estáticos do produto em si. Isso também permite, futuramente, rastrear alterações de versão de uma fórmula sem afetar o cadastro do produto.

A entidade **Matéria_prima** foi modelada separadamente de Formula, conectada por meio do relacionamento "utiliza", porque uma fórmula pode consumir múltiplas matérias-primas em quantidades diferentes — uma relação que não poderia ser representada corretamente como atributos fixos dentro de Formula.

A entidade **Fornecedores** foi mantida separada de Matéria_prima porque fornecedor e matéria-prima são conceitos distintos no negócio: um fornecedor é uma pessoa jurídica com dados próprios (CNPJ, endereço, contato), enquanto a matéria-prima é um insumo da produção. O relacionamento entre as duas entidades foi modelado como (1,1):(1,1) porque, na operação observada na JV Indústria, cada matéria-prima utilizada é adquirida de um fornecedor fixo e exclusivo, sem alternância entre fornecedores diferentes para o mesmo insumo — essa cardinalidade reflete fielmente a prática comercial relatada na entrevista.

A entidade **Máquina** foi modelada como independente porque, na operação observada, cada máquina é dedicada exclusivamente a um tipo de produto. Representar essa regra de negócio exige que Máquina exista como entidade própria, relacionada à Matéria_prima e à Produção, permitindo validar que a fabricação de um produto só ocorra na máquina correspondente.

A entidade **Produção** foi separada de Produto porque representa um evento específico — uma execução real de fabricação, vinculada a um produto, com atributos próprios (quantidade, validade, data de fabricação). Isso reflete diretamente a regra de negócio de que a quantidade produzida só é conhecida (e registrada) após o encerramento da fórmula, podendo divergir da quantidade originalmente planejada. O atributo `id_estoque` presente em Produção foi mantido como forma de vincular diretamente cada registro de produção ao controle de estoque correspondente, funcionando como uma referência cruzada entre as duas entidades — garantindo que, a partir de um registro de produção, seja possível localizar imediatamente sua posição no estoque.

A entidade **Lote** foi criada a partir de Produção para garantir rastreabilidade granular — cada lote carrega número, status, quantidade produzida, validade e data de fabricação próprios, permitindo rastrear fisicamente de onde veio cada unidade de produto que entra em estoque, algo exigido explicitamente pela entrevista ("toda produção recebe número dela e lote e validade dos produtos, data de fabricação").

A entidade **Estoque** foi separada de Lote/Produto porque representa o saldo disponível em determinado momento, atualizado tanto automaticamente ao final da produção quanto manualmente pela conferência da expedição — duas origens de atualização que justificam a entidade ser independente, com seu próprio histórico de atualização.

A entidade **Expedição** foi modelada separadamente de Pedido porque representa uma etapa distinta do processo logístico, com atributos próprios (data de saída, data de entrega, status, endereço de entrega) que ocorrem depois da produção estar concluída — nem todo pedido chega a esse estágio no mesmo momento em que é criado. O relacionamento entre Expedição/Veículo e Lote foi mantido para representar a vinculação do lote produzido ao veículo responsável por sua entrega final, fechando o ciclo de rastreabilidade do produto desde a fabricação até a saída física da empresa.

A entidade **Nota_fiscal** foi mantida separada de Pedido e de Expedição porque, na operação real, a nota fiscal só é emitida após a confirmação da expedição — existe uma defasagem temporal entre os eventos que não seria corretamente representada caso a nota fiscal fosse apenas um atributo de outra entidade. Além disso, a nota fiscal carrega atributos legais próprios (número da nota, data de emissão) que não existem antes de sua emissão efetiva.

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
| **Trechos rejeitados ou corrigidos** | O levantamento original do ChatGPT sugeria tratar "Envase" e "Pallet" como entidades próprias do modelo; o grupo optou por representá-los como etapas do processo produtivo, e não como entidades independentes, para evitar granularidade excessiva no MER. Após a finalização do DER pelo grupo no Figma, algumas cardinalidades e nomes de relacionamentos ainda estão sendo revisados (ex.: cardinalidade entre Fornecedores e Matéria_Prima, e o nome de um relacionamento entre Expedição e Veículo).|
| **Justificativa da escolha final** | A organização por categorias (Entidades/Processos/Regras) facilitou a transição direta desse levantamento para o MER e o dicionário de dados, mantendo rastreabilidade da fala original de onde cada regra foi extraída. |
| **Reflexão crítica** | Como a IA apenas reorganiza e não valida o conteúdo, cabe ao grupo confirmar que nenhuma informação foi mal interpretada na reorganização — por exemplo, distinguir corretamente entre regras aplicáveis a "faturamento" e a "retirada com pagamento à vista", que têm condições diferentes. |

---
