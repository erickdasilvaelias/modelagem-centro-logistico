# Entrega 1 — Modelo Conceitual (DER)
### Modelagem de um sistema de gestão de informações para uma organização de pequeno porte

---

## Metadados

- **Nomes dos alunos e RGM:**
  - Erick da Silva Elias, RGM: 47676779
  - Fabricio Coutinho, RGM: 4795228  
  - Marcella Flandes Souza De Mello, RGM: 48386278
  - Matheus Fagundes
  - Henry Amaral Pires, RGM: 49937707

---

## 1. Caracterização da Organização

- **Nome e natureza da organização:** (Nome da Empresa) Empresa fabricante de materiais para construção civil (argamassas, texturas e afins), que produz sob encomenda conforme pedido do cliente.  (FIZ METADE)

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

- 

### 3.2 Requisitos Não Funcionais

- 

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
 
- **Restrições organizacionais:**
  -  — ex.: exigências legais de transporte de determinadas mercadorias, prazos contratuais com fornecedores, políticas internas de segurança no galpão, normas de armazenagem (empilhamento máximo, produtos perecíveis, etc.

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
| **Ferramenta e etapa** | Claude (Anthropic) — apoio na estruturação do modelo conceitual, elaboração de um diagrama ER de exemplo e organização inicial deste README a partir do esqueleto fornecido pela disciplina. |
| **Motivação** |  por que recorremos à IA |
| **Prompt(s) utilizados** |  reproduzir os prompts reais usados na conversa |
| **Resposta recebida** |  resumir o que a IA gerou |
| **Fontes consultadas e verificadas** |  a IA não citou fontes externas; o conteúdo foi baseado em conhecimento geral de modelagem de dados e precisa ser validado contra o que foi observado na visita de campo |
| **Trechos rejeitados ou corrigidos** |  o que foi ajustado a partir do que a IA sugeriu, especialmente entidades/atributos/regras que não correspondem à organização real |
| **Justificativa da escolha final** | (escrever) |
| **Reflexão crítica** |  ex.: a IA inicialmente sugeriu um modelo para uma empresa fictícia genérica, que precisou ser substituído por uma organização real, pesquisada em campo, conforme exigido pelo enunciado |

---

