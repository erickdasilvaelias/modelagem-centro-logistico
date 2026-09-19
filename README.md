# Entrega 1 — Modelo Conceitual (DER)
### Modelagem de um sistema de gestão de informações para uma organização de pequeno porte

---

## Metadados

- **Nomes dos alunos e RGM:**
  - [PREENCHER — Nome completo, RGM]
  - [PREENCHER — Nome completo, RGM]
  - [PREENCHER — Nome completo, RGM]

---

## 1. Caracterização da Organização

- **Nome e natureza da organização:** [PREENCHER — nome real do centro logístico/distribuidora visitado]. Empresa fabricante de materiais para construção civil (argamassas, texturas e afins), que produz sob encomenda conforme pedido do cliente.  (FIZ METADE)

- **Contexto e porte:** Empresa de pequeno/médio porte, com fins lucrativos. [PREENCHER — número aproximado de funcionários envolvidos na operação: recepção/conferência, estoque, separação, expedição, motoristas, administrativo]. [PREENCHER — volume aproximado de atividades observado: nº de pedidos processados por dia/semana, nº de entregas, nº de fornecedores atendidos, nº de clientes ativos].

- **Problemas e necessidades identificados:** [PREENCHER com base na visita — ex.: controle de estoque feito em planilhas soltas sem integração com os pedidos; falta de rastreabilidade dos produtos entre recebimento e expedição; ausência de histórico centralizado de entregas e motoristas; dificuldade em saber a localização exata de um produto dentro do galpão; retrabalho manual na conferência de notas fiscais e itens].

- **Justificativa da escolha:** [PREENCHER — por que essa organização foi escolhida (acesso garantido, porte adequado, riqueza de processos observáveis: recebimento, estoque, pedidos, entregas)].

- **Evidências da organização:** [PREENCHER —
  - Endereço completo
  - Contato (telefone/e-mail) e nome do responsável entrevistado
  - Link no Google Maps / Google Meu Negócio ou site/rede social
  - Fotos da visita (anexar no repositório, ex.: `/evidencias/`)]

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

  [PREENCHER — ajuste esta lista conforme os processos que vocês efetivamente observaram/confirmaram na visita; remova ou adicione processos específicos dessa empresa]

- **Fluxogramas:** (Opcional) [PREENCHER — se o grupo optar por representar visualmente os processos-chave, anexar as imagens no repositório e referenciá-las aqui, ex.: `![Fluxo de pedidos](./fluxogramas/fluxo_pedidos.png)`]

---

## 3. Requisitos do Sistema

### 3.1 Requisitos Funcionais

- O sistema deve permitir cadastrar, consultar, editar e inativar clientes.
- O sistema deve permitir cadastrar, consultar, editar e inativar fornecedores.
- O sistema deve permitir cadastrar produtos, associando-os a um fornecedor.
- O sistema deve permitir registrar a entrada de produtos no estoque, com localização (setor/prateleira) e quantidade.
- O sistema deve permitir registrar um pedido de cliente, composto por um ou mais itens (produto + quantidade).
- O sistema deve permitir consultar a disponibilidade de estoque de um produto antes de confirmar um pedido.
- O sistema deve permitir registrar a saída de um pedido para entrega, associando veículo e responsável (motorista/funcionário).
- O sistema deve permitir consultar o status de uma entrega (pendente, em rota, entregue).
- O sistema deve permitir gerar relatórios de estoque, pedidos e entregas por período.

[PREENCHER — adicione ou ajuste requisitos conforme as particularidades observadas na organização real]

### 3.2 Requisitos Não Funcionais

- **Desempenho:** o sistema deve responder a consultas de estoque em tempo hábil para não atrasar a separação de pedidos.
- **Disponibilidade:** o sistema deve estar disponível durante o horário de funcionamento do centro logístico.
- **Segurança:** o acesso a dados de clientes e fornecedores deve ser restrito a usuários autorizados.
- **Usabilidade:** a interface deve ser simples o suficiente para uso por funcionários do estoque sem formação técnica em TI.
- **Integridade:** o sistema não deve permitir a confirmação de um pedido cuja quantidade solicitada exceda o estoque disponível.

[PREENCHER — ajuste conforme a realidade observada]

---

## 4. Regras de Negócio   (FIZ METADE)

- **Regras operacionais:**
  - A quantidade produzida de cada produto é determinada exclusivamente pelo pedido do cliente (em kg); não há produção especulativa sem pedido associado.
  - Cada fórmula emitida no sistema corresponde a um único produto e uma única quantidade planejada, definidos a partir do pedido do cliente.
  - Cada máquina é dedicada exclusivamente a um tipo de produto; uma fórmula só pode ser direcionada para a máquina correspondente ao produto solicitado.
  - Uma fórmula só é encerrada no sistema após o registro da quantidade efetivamente produzida.
  - A entrada de produto em estoque só ocorre após a expedição confirmar e registrar a quantidade recebida da produção.
  - A nota fiscal só pode ser emitida após a confirmação da expedição (produto já registrado em estoque).
  - A contratação do veículo de entrega ocorre após a emissão da nota fiscal, vinculada ao pedido correspondente.
  - [PREENCHER — regras específicas observadas na organização real: ex. política de devolução, prazo mínimo para cancelamento de pedido, exigência de nota fiscal, etc.]

- **Restrições organizacionais:**
  - [PREENCHER — ex.: exigências legais de transporte de determinadas mercadorias, prazos contratuais com fornecedores, políticas internas de segurança no galpão, normas de armazenagem (empilhamento máximo, produtos perecíveis, etc.)]

---

## 5. Dicionário de Dados Conceitual (Preliminar)

> Exemplos de valores abaixo são **fictícios**, apenas ilustrativos, coerentes com o que foi observado na visita.

### Cliente

| Atributo | Descrição | Regra de negócio associada |
|----------|-----------|------------------------------|
| id_cliente | Identificador único do cliente | Gerado automaticamente pelo sistema |
| nome | Nome ou razão social do cliente | Obrigatório |
| cnpj_cpf | Documento de identificação fiscal | Obrigatório, único |
| endereco | Endereço de entrega do cliente | Obrigatório |
| telefone | Telefone de contato | Opcional |

### Fornecedor

| Atributo | Descrição | Regra de negócio associada |
|----------|-----------|------------------------------|
| id_fornecedor | Identificador único do fornecedor | Gerado automaticamente pelo sistema |
| razao_social | Nome da empresa fornecedora | Obrigatório |
| cnpj | Documento de identificação fiscal | Obrigatório, único |
| contato | Nome e telefone do responsável | Opcional |

### Produto

| Atributo | Descrição | Regra de negócio associada |
|----------|-----------|------------------------------|
| id_produto | Identificador único do produto | Gerado automaticamente pelo sistema |
| id_fornecedor | Fornecedor responsável pelo produto | Obrigatório, deve existir na tabela de fornecedores |
| nome | Nome do produto | Obrigatório |
| categoria | Categoria/tipo do produto | Obrigatório |
| peso_kg | Peso unitário do produto | Usado para cálculo de capacidade de carga |

### Estoque

| Atributo | Descrição | Regra de negócio associada |
|----------|-----------|------------------------------|
| id_estoque | Identificador único do registro de estoque | Gerado automaticamente pelo sistema |
| id_produto | Produto armazenado | Obrigatório, deve existir na tabela de produtos |
| localizacao | Setor/prateleira onde o produto está | Obrigatório |
| quantidade | Quantidade disponível nessa localização | Não pode ser negativa |

### Pedido

| Atributo | Descrição | Regra de negócio associada |
|----------|-----------|------------------------------|
| id_pedido | Identificador único do pedido | Gerado automaticamente pelo sistema |
| id_cliente | Cliente que fez o pedido | Obrigatório, deve existir na tabela de clientes |
| data_pedido | Data em que o pedido foi realizado | Obrigatório |
| status | Situação do pedido (aberto, separado, entregue, cancelado) | Só pode assumir valores predefinidos |
| valor_total | Valor total do pedido | Calculado a partir dos itens |

### Item_Pedido

| Atributo | Descrição | Regra de negócio associada |
|----------|-----------|------------------------------|
| id_item | Identificador único do item | Gerado automaticamente pelo sistema |
| id_pedido | Pedido ao qual o item pertence | Obrigatório |
| id_produto | Produto solicitado | Obrigatório, deve existir na tabela de produtos |
| quantidade | Quantidade solicitada do produto | Não pode exceder o estoque disponível no fechamento do pedido |
| preco_unitario | Preço do produto no momento do pedido | Obrigatório |

### Entrega

| Atributo | Descrição | Regra de negócio associada |
|----------|-----------|------------------------------|
| id_entrega | Identificador único da entrega | Gerado automaticamente pelo sistema |
| id_pedido | Pedido associado à entrega | Obrigatório, único (um pedido gera no máximo uma entrega) |
| id_veiculo | Veículo utilizado na entrega | Obrigatório |
| data_saida | Data de saída do centro logístico | Obrigatório |
| data_entrega | Data em que a entrega foi concluída | Preenchido ao final da entrega |
| status_entrega | Situação da entrega (pendente, em rota, entregue) | Só pode assumir valores predefinidos |

### Veiculo

| Atributo | Descrição | Regra de negócio associada |
|----------|-----------|------------------------------|
| id_veiculo | Identificador único do veículo | Gerado automaticamente pelo sistema |
| id_funcionario | Motorista responsável pelo veículo | Obrigatório |
| placa | Placa do veículo | Obrigatória, única |
| modelo | Modelo do veículo | Obrigatório |
| capacidade_kg | Capacidade máxima de carga | Usada para validar se comporta o peso do pedido |

### Funcionario

| Atributo | Descrição | Regra de negócio associada |
|----------|-----------|------------------------------|
| id_funcionario | Identificador único do funcionário | Gerado automaticamente pelo sistema |
| nome | Nome do funcionário | Obrigatório |
| cargo | Função exercida (motorista, estoquista, conferente) | Obrigatório |
| cnh | Número da CNH, se aplicável | Obrigatório apenas para motoristas |

[PREENCHER — ajuste atributos/entidades conforme o que foi realmente observado na organização; remova entidades que não se aplicam ou adicione as que forem específicas]

---

## 6. Modelagem Conceitual (Entidades, Atributos, Relacionamentos)

- **Entidades reconhecidas:** Cliente, Fornecedor, Produto, Estoque, Pedido, Item_Pedido, Entrega, Veículo, Funcionário.
  [PREENCHER — justificar brevemente cada uma com base no que foi observado: por que essa entidade é necessária para representar a operação real da organização]

- **Atributos e classificações:** ver Dicionário de Dados (Seção 5).

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

- DER anexado em imagem no repositório: [PREENCHER — caminho do arquivo, ex. `/der/der_centro_logistico.png`]
- O diagrama representa entidades, atributos, relacionamentos e cardinalidades (notação BR / min-máx), conforme elaborado a partir do levantamento de requisitos.

---

## 8. Justificativa Técnica

[PREENCHER — Explique e defenda as decisões de abstração tomadas: por que essas entidades específicas (e não outras), por que esses atributos, por que essas cardinalidades. Por exemplo: por que Entrega foi modelada como entidade separada de Pedido em vez de atributos do próprio pedido; por que Item_Pedido existe como entidade associativa em vez de relacionamento direto N:N entre Pedido e Produto; por que Estoque foi separado de Produto (permite múltiplas localizações por produto).]

---

## 9. Uso de Inteligência Artificial

| Item | Registro |
|------|------------------|
| **Ferramenta e etapa** | Claude (Anthropic) — apoio na estruturação do modelo conceitual, elaboração de um diagrama ER de exemplo e organização inicial deste README a partir do esqueleto fornecido pela disciplina. |
| **Motivação** | [PREENCHER — por que o grupo recorreu à IA] |
| **Prompt(s) utilizados** | [PREENCHER — reproduzir os prompts reais usados na conversa] |
| **Resposta recebida** | [PREENCHER — resumir o que a IA gerou] |
| **Fontes consultadas e verificadas** | [PREENCHER — a IA não citou fontes externas; o conteúdo foi baseado em conhecimento geral de modelagem de dados e precisa ser validado contra o que foi observado na visita de campo] |
| **Trechos rejeitados ou corrigidos** | [PREENCHER — o que foi ajustado a partir do que a IA sugeriu, especialmente entidades/atributos/regras que não correspondem à organização real] |
| **Justificativa da escolha final** | [PREENCHER] |
| **Reflexão crítica** | [PREENCHER — ex.: a IA inicialmente sugeriu um modelo para uma empresa fictícia genérica, que precisou ser substituído por uma organização real, pesquisada em campo, conforme exigido pelo enunciado] |

---

