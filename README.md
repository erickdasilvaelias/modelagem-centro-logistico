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
- **Rastreabilidade:** o sistema deve manter o histórico de cada lote produzido, vinculado à produção de origem (e, por meio dela, à fórmula e à máquina) e ao pedido atendido (por meio da entrega).

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
| CLIENTE | PEDIDO | 1:N — um cliente realiza vários pedidos; todo pedido pertence a um único cliente |
| PEDIDO | NOTA_FISCAL | 1:1 — um pedido origina uma nota fiscal (verbo *emitir*) |
| PEDIDO | ENTREGA | 1:1 opcional — um pedido pode ou não gerar uma entrega (verbo *informa*); toda entrega pertence a um único pedido |
| PEDIDO | PRODUTO | N:N — um pedido tem de 1 a N produtos; um produto está em 0 a N pedidos (verbo *origina*; resolvido por ITEM_PEDIDO) |
| ENTREGA | VEICULO | N:N — uma entrega usa de 1 a N veículos; um veículo faz 0 a N entregas (verbo *utiliza*; resolvido por ENTREGA_VEICULO) |
| ENTREGA | LOTE | 1:N — uma entrega envia de 1 a N lotes; cada lote segue em uma única entrega (verbo *envia*) |
| PRODUTO | FORMULA | 1:N — um produto possui de 1 a N fórmulas (versões); cada fórmula pertence a um único produto (verbo *possui*) |
| PRODUTO | PRODUCAO | 1:N — um produto é fabricado em 0 a N produções; cada produção produz um único produto (verbo *produz*) |
| PRODUCAO | LOTE | 1:N — uma produção gera 0 a N lotes; cada lote vem de uma única produção (verbo *fabricar*) |
| EMBALAGEM | LOTE | 1:N — uma embalagem é usada em 1 a N lotes; cada lote tem exatamente uma embalagem (verbo *embala*) |
| PRODUCAO | MAQUINA | N:N — uma produção usa de 1 a N máquinas; uma máquina realiza 0 a N produções (verbo *realiza*; resolvido por PRODUCAO_MAQUINA) |
| MATERIA_PRIMA | MAQUINA | N:N — uma matéria-prima abastece 1 a N máquinas e vice-versa (verbo *abastece*; resolvido por ABASTECIMENTO) |
| MATERIA_PRIMA | FORNECEDOR | N:N — fornecedores e matérias-primas se relacionam por 0 a N compras (verbo *compra*; resolvido por COMPRA) |
| PRODUCAO + FORMULA + MATERIA_PRIMA | — | Ternário — cada produção aplica uma fórmula que consome matérias-primas (verbo *Utiliza*; resolvido por UTILIZACAO) |
| ESTOQUE | MOVIMENTO_ESTOQUE | 1:N — um estoque é atualizado por 0 a N movimentos; todo movimento afeta exatamente um estoque (verbo *atualiza*) |
| ESTOQUE + MATERIA_PRIMA + PRODUTO + LOTE | — | Quaternário — o estoque registra matérias-primas, produtos e lotes (verbo *registra*; resolvido por REGISTRO_ESTOQUE) |

**Definições das entidades**

- **Cliente** é a pessoa física ou jurídica que adquire produtos por meio de pedidos.
- **Pedido** é a solicitação de compra feita por um cliente, com valores, forma de pagamento e prazos de entrega.
- **Nota fiscal** é o documento fiscal emitido a partir de um pedido.
- **Entrega** é o evento de transporte de lotes até o cliente, com código de rastreio.
- **Veículo** é o meio de transporte utilizado nas entregas.
- **Produto** é o item fabricado e comercializado pela empresa.
- **Fórmula** é a receita versionada que define como um produto é fabricado.
- **Matéria-prima** é o insumo adquirido de fornecedores e consumido na produção.
- **Fornecedor** é a pessoa jurídica que vende matéria-prima à empresa.
- **Máquina** é o equipamento que executa a fabricação e é abastecido por matérias-primas.
- **Produção** é o evento de fabricação de um produto, com data e validade.
- **Lote** é o conjunto de unidades resultante de uma produção, embalado e enviado em conjunto.
- **Embalagem** é o recipiente ou invólucro (tipo e tamanho) usado nos lotes.
- **Estoque** é o local de armazenagem de matérias-primas, produtos e lotes.
- **Movimento no estoque** é o registro de entrada ou saída que atualiza um estoque.
---

## 2. Fluxo de dados (visão de DFD)

Fornecedor entrega matéria-prima → **COMPRA** registra a aquisição e **REGISTRO_ESTOQUE** lança a matéria-prima no **ESTOQUE** → a matéria-prima **abastece** a **MAQUINA** → uma **PRODUCAO** é executada com uma **FORMULA** do **PRODUTO**, consumindo matérias-primas (**UTILIZACAO**) nas máquinas escolhidas (**PRODUCAO_MAQUINA**) → a produção gera **LOTE**s, cada um com sua **EMBALAGEM**, que voltam ao **ESTOQUE** via **REGISTRO_ESTOQUE** e geram **MOVIMENTO_ESTOQUE** → o **CLIENTE** faz um **PEDIDO** com seus itens (**ITEM_PEDIDO**) → o pedido origina a **NOTA_FISCAL** e, quando há entrega, uma **ENTREGA** que envia os lotes por **VEICULO**s (**ENTREGA_VEICULO**) → a saída baixa o estoque por novo **MOVIMENTO_ESTOQUE** → toda leitura ou escrita nessas tabelas é registrada pelo log de acesso do SGBD (§5), o que sustenta auditoria e conformidade com a LGPD (§6).




## 6. Modelagem Conceitual (Entidades, Atributos, Relacionamentos)

- **Entidades reconhecidas:** Cliente, Pedido, Nota_Fiscal, Produto, Estoque, Movimento_Estoque, Formula, Matéria_Prima, Fornecedor, Máquina, Produção, Lote, Embalagem, Entrega, Veículos. Cada entidade corresponde a uma etapa ou elemento concreto identificado no processo real da empresa: desde o pedido do cliente até a entrega final, passando pela emissão da fórmula, consumo de matéria-prima, fabricação em máquina, controle de lote, estoque e faturamento.

- **Relacionamentos pertinentes:**
  - Cliente **realiza** Pedido (0,N) : (1,1) — Um cliente pode realizar nenhum ou vários pedidos, mas cada pedido pertence a um único cliente.
  - Pedido **emite** Nota_Fiscal (1,1) : (0,1) — Cada pedido gera exatamente uma nota fiscal, e cada nota fiscal está associada a no máximo um pedido.
  - Pedido **origina** Produto (1,N) : (0,N) — Um pedido deve conter de um a vários produtos, e um produto pode estar presente em nenhum ou vários pedidos (relacionamento N:N, resolvido no modelo lógico pela tabela associativa Item_Pedido).
  - Produto **possui** Formula (1,N) : (1,1) — Um produto possui de uma a várias fórmulas (versões), e cada fórmula pertence a um único produto.
  - Produção **produz** Produto (1,1) : (0,N) — Cada produção produz exatamente um produto, e um produto pode ser fabricado em nenhuma ou várias produções.
  - Formula **utiliza** Matéria_Prima, em uma Produção (relacionamento ternário) — Formula (1,N), Matéria_Prima (1,N) e Produção (1,1) no DER: uma fórmula utiliza uma ou várias matérias-primas, uma matéria-prima pode ser usada em uma ou várias fórmulas, e cada utilização ocorre no contexto de exatamente uma produção.
  - Matéria_Prima **abastece** Máquina (1,N) : (1,N) — Uma matéria-prima abastece uma ou várias máquinas, e cada máquina é abastecida por uma ou várias matérias-primas.
  - Matéria_Prima **é fornecida por** Fornecedor (0,N) : (0,N) — Uma matéria-prima pode ser comprada de nenhum ou vários fornecedores, e um fornecedor pode fornecer nenhuma ou várias matérias-primas (relacionamento *compra* no DER).
  - Máquina **realiza** Produção (0,N) : (1,N) — Uma máquina pode realizar nenhuma ou várias produções, e cada produção é realizada por uma ou várias máquinas.
  - Produção **fabrica** Lote (0,N) : (1,1) — Uma produção pode gerar nenhum ou vários lotes, e cada lote vem de exatamente uma produção.
  - Embalagem **embala** Lote (1,N) : (1,1) — Uma embalagem embala um ou vários lotes, e cada lote possui exatamente uma embalagem.
  - Estoque **registra** Matéria_Prima, Produto e Lote (relacionamento quaternário) — Estoque (1,N), Matéria_Prima (0,N), Produto (0,N) e Lote (0,N) no DER: cada matéria-prima, produto ou lote pode constar em nenhum ou vários registros de estoque, e todo registro envolve ao menos um estoque.
  - Estoque **é atualizado por** Movimento_Estoque (0,N) : (1,1) — Um estoque pode ser atualizado por nenhuma ou múltiplas movimentações ao longo do tempo, e cada movimentação atualiza exatamente um estoque (relacionamento *atualiza* no DER).
  - Pedido **informa** Entrega (0,1) : (1,1) — Um pedido pode gerar nenhuma ou uma entrega (retirada no local não gera entrega), e cada entrega atende a exatamente um pedido.
  - Entrega **envia** Lote (1,N) : (1,1) — Uma entrega envia um ou vários lotes, e cada lote segue em exatamente uma entrega.
  - Entrega **utiliza** Veículos (1,N) : (0,N) — Uma entrega utiliza um ou vários veículos, e um veículo pode participar de nenhuma ou várias entregas.

- **Restrições e políticas organizacionais aplicadas ao modelo:**
  - A obrigatoriedade de todo Produto possuir ao menos uma Formula (1,N) reflete a regra de que cada produto possui fórmula própria, que não muda entre pedidos; a cardinalidade N admite apenas versões da mesma fórmula (atributo versão), sem alterar o cadastro do produto.
  - A obrigatoriedade de cada Lote vir de exatamente uma Produção (1,1) — que, por sua vez, produz exatamente um Produto (1,1) — reflete a regra de que toda produção recebe número, lote, validade e data de fabricação, garantindo rastreabilidade por lote até um único produto.
  - A existência de Movimento_Estoque como entidade própria, associada a Estoque, permite registrar tanto a entrada automática de produtos ao final da produção quanto a confirmação manual feita pela expedição.
  - A cardinalidade (0,1):(1,1) entre Pedido e Entrega permite pedidos sem entrega (retirada no local) e garante que cada entrega atenda a um único pedido, enquanto a cardinalidade (1,N):(0,N) entre Entrega e Veículos permite que uma entrega use mais de um veículo contratado e que um veículo atenda várias entregas ao longo do tempo; a regra de que a entrega só ocorre após a emissão da nota fiscal é de processo e não aparece nas cardinalidades.


## 7. Diagrama Entidade-Relacionamento (DER)

![DER - JV Indústria](img/der.jpg)

O diagrama acima representa as entidades, atributos, relacionamentos e cardinalidades levantados a partir do processo produtivo da JV Indústria, cobrindo desde o recebimento do pedido do cliente até a entrega final — passando pela emissão de fórmula, consumo de matéria-prima, fabricação em máquina, controle de lote, entrada e movimentação em estoque, e faturamento.

**Entidades representadas:** Cliente, Pedido, Nota_Fiscal, Produto, Estoque, Movimento_Estoque, Formula, Matéria_Prima, Fornecedor, Máquina, Produção, Lote, Embalagem, Entrega, Veículos.

---

## 8. Justificativa Técnica

Pedido e Produto foram ligados no DER por um relacionamento direto N:N (*origina*), porque um mesmo pedido pode conter múltiplos produtos e um mesmo produto pode aparecer em múltiplos pedidos diferentes, conforme a realidade observada. Na passagem para o modelo lógico, esse relacionamento será resolvido por uma tabela associativa (**Item_Pedido**), que poderá carregar informações próprias de cada item (quantidade solicitada, por exemplo), pois elas não pertencem exclusivamente nem ao Pedido nem ao Produto isoladamente.

A entidade **Nota_Fiscal** foi mantida separada de Pedido porque representa um documento fiscal com atributos próprios (número da nota, data de emissão) e um momento distinto no processo — a emissão da nota ocorre após a confirmação da produção/estoque, e não no momento em que o pedido é criado.

A entidade **Formula** foi separada de Produto porque, apesar de cada produto possuir uma fórmula própria e fixa (conforme relatado na entrevista), a fórmula representa um processo com atributos e ciclo de vida próprios — status, versão, data de emissão — que não fazem sentido como atributos estáticos do produto em si. Isso também permite, futuramente, rastrear alterações de versão de uma fórmula sem afetar o cadastro do produto.

A entidade **Matéria_Prima** foi modelada separadamente de Formula, conectada por meio do relacionamento "utiliza", porque uma fórmula pode consumir múltiplas matérias-primas em quantidades diferentes — uma relação que não poderia ser representada corretamente como atributos fixos dentro de Formula.

A entidade **Máquina** foi modelada como independente porque, na operação observada, cada máquina é dedicada exclusivamente a um tipo de produto. Representar essa regra de negócio exige que Máquina exista como entidade própria, relacionada à Matéria_Prima (abastece) e à Produção (realiza), permitindo rastrear, por meio da Produção, qual máquina fabricou determinado lote.

A entidade **Lote** foi criada para garantir rastreabilidade granular — cada lote carrega número, status e quantidade próprios e, por meio da Produção de origem, data de fabricação e validade, permitindo rastrear fisicamente de onde veio cada unidade de produto que entra em estoque, algo exigido explicitamente pela entrevista ("toda produção recebe número dela e lote e validade dos produtos, data de fabricação").

A entidade **Estoque** foi separada de Produto porque representa o local de armazenagem (localidade) em que matérias-primas, produtos e lotes são registrados, e não uma característica fixa do produto. A entidade **Movimento_Estoque** foi criada separadamente de Estoque para registrar o histórico de alterações de quantidade ao longo do tempo (entradas, saídas, ajustes), permitindo rastrear quando e por que o saldo de um produto mudou — algo que o Estoque, que guarda apenas a localidade, não conseguiria representar.

A entidade **Entrega** foi modelada separadamente de Pedido porque representa uma etapa distinta do processo logístico, que ocorre somente após a emissão da nota fiscal, com atributos próprios relacionados ao transporte. A entidade **Veículos** foi mantida separada de Entrega porque representa um recurso físico da empresa, com atributos próprios (placa, modelo), que pode ser consultado e gerenciado independentemente de uma entrega específica.

Em conjunto, essas decisões priorizam a **rastreabilidade** de ponta a ponta do processo produtivo — do pedido do cliente até a entrega final — em detrimento de um modelo mais simplificado, já que a própria operação da JV Indústria exige esse nível de controle (produção sob encomenda, dedicação de máquinas por produto, rastreamento por lote e validade, e histórico de movimentação de estoque).

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
