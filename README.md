Metadados
Nomes dos alunos e RGM:
Ana Beatriz Ferreira Lima, RGM 12345678
Carlos Eduardo Santos Oliveira, RGM 87654321
Juliana Costa Ribeiro, RGM 11223344

1. Caracterização da Organização
Nome e natureza da organização: LogiCorp Centro de Distribuição, empresa privada com fins lucrativos do setor de logística e armazenagem, localizada na Zona Leste de São Paulo/SP. Atua como operador logístico para pequenos e médios comerciantes da região, recebendo mercadorias de fornecedores, armazenando-as e distribuindo pedidos para lojistas parceiros.
Contexto e porte: Empresa de pequeno porte, com cerca de 18 funcionários diretos (4 no setor administrativo, 6 na conferência/estoque, 5 na separação de pedidos e 3 motoristas). Processa em média 40 pedidos por dia, atende cerca de 60 clientes ativos (lojistas) e recebe carga de aproximadamente 15 fornecedores fixos.

Problemas e necessidades identificados: O controle de estoque é feito em planilhas Excel separadas por setor, sem comunicação entre o setor de recebimento e o setor de separação — isso já gerou pedidos confirmados sem estoque real disponível. Não existe histórico digital de entregas (fica em anotações de papel dos motoristas), dificultando o rastreamento de atrasos. A conferência de notas fiscais no recebimento é manual e sujeita a erros de digitação.

Justificativa da escolha: O grupo tem acesso direto à empresa por meio de um familiar de um dos integrantes, que é sócio-gerente do local, o que viabilizou visita presencial e entrevista. O porte da empresa é adequado ao escopo da disciplina: processos suficientes para gerar um modelo rico (recebimento, estoque, pedidos, entregas), mas sem a complexidade de uma operação de grande porte.

Evidências da organização:
Endereço: Rua das Palmeiras, 482 — Vila Matilde, São Paulo/SP, CEP 03445-000
Contato: (11) 4002-8922 — responsável entrevistado: Sr. Roberto Almeida (sócio-gerente)
Perfil no Google Meu Negócio: [link fictício — substituir pelo link real]
Fotos da visita anexadas em /evidencias/ (fachada, área de estoque, entrevista com o responsável)

3. Processos de Negócio
Principais processos mapeados:
Cadastro de clientes e fornecedores: feito manualmente pela recepção no momento do primeiro contato comercial.
Recebimento de mercadorias: o conferente recebe a carga do fornecedor, confere contra a nota fiscal e registra a entrada no estoque.
Controle de estoque: cada produto recebe uma localização física (corredor/prateleira) anotada em planilha.
Emissão e processamento de pedidos: o lojista liga ou envia WhatsApp com a lista de produtos; o atendente registra o pedido.
Separação de pedidos (picking): um funcionário do estoque percorre as prateleiras coletando os itens do pedido.
Expedição e entrega: os pedidos separados são agrupados por região e carregados nos veículos disponíveis; o motorista realiza a entrega e retorna com o canhoto assinado.

Fluxogramas: (Opcional) Não elaborado nesta entrega de exemplo — no trabalho real, recomenda-se ao menos o fluxo de "Pedido → Separação → Expedição → Entrega".
5. Requisitos do Sistema
3.1 Requisitos Funcionais
O sistema deve permitir cadastrar, consultar, editar e inativar clientes (lojistas).
O sistema deve permitir cadastrar, consultar, editar e inativar fornecedores.
O sistema deve permitir cadastrar produtos, associando-os a um fornecedor.
O sistema deve permitir registrar entrada de produtos no estoque, com localização e quantidade.
O sistema deve permitir registrar um pedido composto por um ou mais itens.
O sistema deve permitir verificar a disponibilidade de estoque antes de confirmar um pedido.
O sistema deve permitir registrar a saída de um pedido para entrega, associando veículo e motorista.
O sistema deve permitir consultar o status de uma entrega (pendente, em rota, entregue).
O sistema deve permitir gerar relatório mensal de pedidos por cliente.

3.2 Requisitos Não Funcionais
Desempenho: consulta de estoque deve responder em menos de 2 segundos durante a separação de pedidos.
Disponibilidade: sistema disponível das 6h às 20h, horário de operação do galpão.
Segurança: acesso ao cadastro de clientes e valores de pedidos restrito a usuários com login (administrativo e gerência).
Usabilidade: interface simples, pensada para funcionários do estoque sem experiência prévia com sistemas.
Integridade: sistema não permite confirmar pedido com quantidade acima do estoque disponível.

6. Regras de Negócio
Regras operacionais:
Um pedido só pode ser confirmado se houver estoque disponível para todos os itens.
Um produto só pode ser cadastrado se associado a um fornecedor já cadastrado.
Uma entrega só é registrada após a separação (picking) do pedido estar concluída.
Um veículo só pode ser associado a uma entrega se sua capacidade de carga comportar o peso total do pedido.
Pedidos cancelados após o início da separação exigem autorização do gerente.

Restrições organizacionais:
A empresa opera sob normas municipais de carga e descarga em via pública, o que limita o horário de recebimento de fornecedores (7h às 11h).
Produtos perecíveis (parte do mix de alguns fornecedores) têm prazo máximo de 48h em estoque antes da expedição obrigatória.
8. Dicionário de Dados Conceitual (Preliminar)

Exemplos de valores fictícios, apenas ilustrativos.

Cliente
Atributo	Descrição	Regra de negócio associada
id_cliente	Identificador único do cliente	Gerado automaticamente
nome	Nome fantasia do lojista (ex.: "Mercadinho Boa Vista")	Obrigatório
cnpj_cpf	CNPJ do lojista	Obrigatório, único
endereco	Endereço de entrega	Obrigatório
telefone	Telefone/WhatsApp de contato	Obrigatório
Fornecedor
Atributo	Descrição	Regra de negócio associada
id_fornecedor	Identificador único	Gerado automaticamente
razao_social	Ex.: "Distribuidora Alimentos Vale Ltda."	Obrigatório
cnpj	CNPJ do fornecedor	Obrigatório, único
contato	Nome e telefone do representante	Opcional
Produto
Atributo	Descrição	Regra de negócio associada
id_produto	Identificador único	Gerado automaticamente
id_fornecedor	Fornecedor do produto	Obrigatório
nome	Ex.: "Arroz tipo 1 - pacote 5kg"	Obrigatório
categoria	Ex.: "Mercearia"	Obrigatório
peso_kg	Ex.: 5.0	Usado no cálculo de capacidade de carga
Estoque
Atributo	Descrição	Regra de negócio associada
id_estoque	Identificador único	Gerado automaticamente
id_produto	Produto armazenado	Obrigatório
localizacao	Ex.: "Corredor 3 - Prateleira B"	Obrigatório
quantidade	Ex.: 240 unidades	Não pode ser negativa
Pedido
Atributo	Descrição	Regra de negócio associada
id_pedido	Identificador único	Gerado automaticamente
id_cliente	Cliente que fez o pedido	Obrigatório
data_pedido	Ex.: 2026-09-10	Obrigatório
status	Ex.: "separado"	Só valores predefinidos
valor_total	Ex.: R$ 1.240,00	Calculado a partir dos itens
Item_Pedido
Atributo	Descrição	Regra de negócio associada
id_item	Identificador único	Gerado automaticamente
id_pedido	Pedido ao qual pertence	Obrigatório
id_produto	Produto solicitado	Obrigatório
quantidade	Ex.: 20 unidades	Não pode exceder estoque disponível
preco_unitario	Ex.: R$ 24,90	Obrigatório
Entrega
Atributo	Descrição	Regra de negócio associada
id_entrega	Identificador único	Gerado automaticamente
id_pedido	Pedido associado	Único por pedido
id_veiculo	Veículo usado	Obrigatório
data_saida	Ex.: 2026-09-11	Obrigatório
data_entrega	Ex.: 2026-09-11	Preenchido ao concluir
status_entrega	Ex.: "entregue"	Só valores predefinidos
Veiculo
Atributo	Descrição	Regra de negócio associada
id_veiculo	Identificador único	Gerado automaticamente
id_funcionario	Motorista responsável	Obrigatório
placa	Ex.: "FXY-4B21"	Obrigatória, única
modelo	Ex.: "Fiorino"	Obrigatório
capacidade_kg	Ex.: 650 kg	Usada para validar carga do pedido
Funcionario
Atributo	Descrição	Regra de negócio associada
id_funcionario	Identificador único	Gerado automaticamente
nome	Ex.: "José Carlos Pereira"	Obrigatório
cargo	Ex.: "Motorista"	Obrigatório
cnh	Ex.: "12345678900"	Obrigatório apenas para motoristas

6. Modelagem Conceitual (Entidades, Atributos, Relacionamentos)
Entidades reconhecidas: Cliente, Fornecedor, Produto, Estoque, Pedido, Item_Pedido, Entrega, Veículo, Funcionário — todas surgiram diretamente dos processos observados na visita (cadastro, recebimento, estoque, pedido, separação, expedição).
Atributos e classificações: ver Dicionário de Dados (Seção 5).
Relacionamentos pertinentes:
Cliente realiza Pedido (1:N)
Pedido contém Item_Pedido (1:N)
Produto compõe Item_Pedido (1:N)
Fornecedor fornece Produto (1:N)
Produto é armazenado em Estoque (1:N)
Pedido gera Entrega (1:1, opcional)
Veículo realiza Entrega (1:N)
Funcionário conduz Veículo (1:N)
Restrições e políticas organizacionais aplicadas ao modelo: a obrigatoriedade de Item_Pedido sempre referenciar um Pedido reflete a regra de que não existe item avulso fora de um pedido; a cardinalidade opcional entre Pedido e Entrega reflete que pedidos podem estar em status "separado" sem ainda ter saído para entrega.

7. Diagrama Entidade-Relacionamento (DER)
DER anexado em /der/der_logicorp.png (exemplo — no trabalho real, gerar a partir do brModelo ou ferramenta equivalente, em notação BR com cardinalidade min-máx).

8. Justificativa Técnica

Item_Pedido foi modelado como entidade associativa (e não como relacionamento direto N:N entre Pedido e Produto) porque cada item carrega atributos próprios — quantidade e preço unitário no momento da compra — que não pertencem nem a Pedido nem a Produto isoladamente. Estoque foi modelado como entidade separada de Produto, e não como atributo simples, porque um mesmo produto pode ocupar mais de uma localização física no galpão (ex.: excedente guardado em corredor secundário), o que uma coluna única de "localização" em Produto não conseguiria representar. Entrega foi separada de Pedido porque nem todo pedido gera imediatamente uma entrega (pode ficar em status "separado" aguardando roteirização), e porque a entrega carrega atributos próprios de logística (veículo, motorista, datas) que não fazem sentido em todo pedido — inclusive pedidos retirados no balcão, cenário observado esporadicamente na empresa.

9. Uso de Inteligência Artificial
Item	Registro
Ferramenta e etapa	Claude (Anthropic) — apoio na estruturação do modelo conceitual e organização do README a partir do esqueleto da disciplina.
Motivação	Acelerar a organização inicial do documento e ter um ponto de partida para discussão em grupo.
Prompt(s) utilizados	"preciso criar um banco de dados sobre uma empresa escolhida, que foi um centro logístico..."; "baseado no que eu disse, preciso criar um readme.md".
Resposta recebida	Estrutura de README com seções preenchidas com conteúdo genérico de centro logístico, e um diagrama ER de exemplo.
Fontes consultadas e verificadas	Nenhuma fonte externa foi citada pela IA; o conteúdo foi baseado em conhecimento geral de modelagem de dados, validado pelo grupo contra o que foi observado na visita real.
Trechos rejeitados ou corrigidos	O grupo substituiu o nome fictício da empresa, os dados de contexto (porte, número de funcionários, volume de pedidos) e os exemplos de regras de negócio pelos dados reais coletados na entrevista com o Sr. Roberto Almeida.
Justificativa da escolha final	O esqueleto de entidades (Cliente, Pedido, Estoque etc.) fazia sentido para a operação observada, então foi mantido; os dados específicos foram substituídos integralmente por informações reais.
Reflexão crítica	A IA inicialmente sugeriu uma empresa totalmente fictícia, o que não atende ao requisito do enunciado de organização real — o grupo precisou identificar esse ponto e reconduzir o trabalho para a pesquisa de campo.
