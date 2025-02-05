# 💻 Projeto de Modelagem de Banco de Dados para E-commerce 🛒

🚀 **Desafio de Modelagem de Banco de Dados para E-commerce** 🚀  
Neste projeto, vamos criar um modelo de banco de dados para um sistema de e-commerce com base nas especificações fornecidas. A modelagem foi feita utilizando **MySQL Workbench**, e inclui as entidades **Cliente**, **Produto**, **Estoque**, **Pedido**, e **Fornecedor**, além de suas relações. Vamos começar!

## 🔧 Preparando o Ambiente

1. Abra o **MySQL Workbench** no seu computador.
2. Crie um novo modelo de banco de dados.
3. Defina as tabelas e seus relacionamentos conforme as especificações a seguir.

## 🧩 Estrutura do Banco de Dados

### **Entidades Principais**

#### **1. Cliente**
- Atributos:
  - `id_cliente`: Identificador único.
  - `nome`: Nome do cliente.
  - `cpf_cnpj`: CPF ou CNPJ, sendo que um cliente pode ser PF ou PJ, mas não ambos.
  - `email`: Endereço de email.
  - `telefone`: Número de telefone.
  - `endereco`: Endereço para cálculo do frete.
  - `tipo_cliente`: "PF" ou "PJ" para diferenciar pessoa física de jurídica.
  - `carencia_devolucao`: Período de carência para devolução.

#### **2. Produto**
- Atributos:
  - `id_produto`: Identificador único.
  - `nome_produto`: Nome do produto.
  - `descricao`: Descrição detalhada do produto.
  - `preco`: Preço de venda.
  - `quantidade_estoque`: Quantidade disponível no estoque.
  - `id_fornecedor`: Relacionamento com o fornecedor do produto.

#### **3. Estoque**
- Atributos:
  - `id_estoque`: Identificador único.
  - `id_produto`: Relacionamento com o produto.
  - `quantidade_disponivel`: Quantidade disponível do produto.
  - `id_fornecedor`: Relacionamento com o fornecedor responsável pelo estoque.

#### **4. Pedido**
- Atributos:
  - `id_pedido`: Identificador único do pedido.
  - `id_cliente`: Relacionamento com o cliente.
  - `data_pedido`: Data em que o pedido foi realizado.
  - `status`: Status do pedido (ex.: "Em Processamento", "Enviado", "Cancelado").
  - `endereco_entrega`: Endereço para a entrega do pedido.
  - `valor_total`: Valor total do pedido.
  - `codigo_rastreio`: Código de rastreio para o pedido.
  - `id_pagamento`: Relacionamento com a tabela de pagamento.

#### **5. Fornecedor**
- Atributos:
  - `id_fornecedor`: Identificador único do fornecedor.
  - `nome_fornecedor`: Nome do fornecedor.
  - `cnpj`: CNPJ do fornecedor.
  - `endereco_fornecedor`: Endereço do fornecedor.
  - `telefone_fornecedor`: Número de telefone do fornecedor.

### **6. Pagamento**
- Atributos:
  - `id_pagamento`: Identificador único do pagamento.
  - `id_pedido`: Relacionamento com o pedido.
  - `metodo_pagamento`: Forma de pagamento (ex.: "Cartão de Crédito", "Boleto", "Transferência").
  - `valor_pago`: Valor pago pelo cliente.
  - `status_pagamento`: Status do pagamento (ex.: "Pendente", "Aprovado", "Cancelado").

### **7. Entrega**
- Atributos:
  - `id_entrega`: Identificador único da entrega.
  - `id_pedido`: Relacionamento com o pedido.
  - `status_entrega`: Status da entrega (ex.: "Em Rota", "Entregue").
  - `codigo_rastreio`: Código de rastreio da entrega.

## 🔗 Relacionamentos Entre as Tabelas

Agora, vamos definir as relações entre as tabelas de acordo com as especificações:

- **Cliente** 1---* **Pedido**  
  Cada cliente pode fazer vários pedidos, mas cada pedido pertence a um único cliente.

- **Produto** *---* **Pedido**  
  Um pedido pode conter vários produtos e um produto pode estar em vários pedidos. (Relacionamento N:N)

- **Produto** 1---* **Fornecedor**  
  Cada produto tem um único fornecedor.

- **Estoque** 1---* **Produto**  
  Cada produto está relacionado a um estoque.

- **Fornecedor** 1---* **Produto**  
  Cada fornecedor pode fornecer vários produtos.

- **Pedido** 1---1 **Pagamento**  
  Cada pedido tem um único pagamento associado.

- **Pedido** 1---1 **Entrega**  
  Cada pedido tem uma única entrega associada.

### Tabela de Relacionamento (Pedido_Produto)

Para o relacionamento N:N entre **Pedido** e **Produto**, criamos uma tabela de relacionamento:

- **Item_Pedido**
  - `id_pedido`: Relacionamento com o pedido.
  - `id_produto`: Relacionamento com o produto.
  - `quantidade`: Quantidade do produto no pedido.
  - `preco_unitario`: Preço unitário do produto na época da compra.

## 🎯 Resultados Obtidos

Após criar as tabelas e definir os relacionamentos, o modelo de banco de dados para o e-commerce estará completo. O diagrama EER criado no MySQL Workbench será uma representação visual da estrutura, facilitando a compreensão do fluxo de dados no sistema.

### 👀 Veja como ficou o Diagrama EER:
![Diagrama EER](./assets/img/Modelo%20E-commerce.png)

## ✨ Conclusão

Esse projeto de modelagem de banco de dados para e-commerce oferece uma base sólida para o desenvolvimento do sistema. A relação entre **Cliente**, **Produto**, **Estoque**, **Pedido**, **Fornecedor**, **Pagamento** e **Entrega** está bem definida, permitindo a implementação de funcionalidades essenciais para um e-commerce.

## 🏞️ Links Importantes

Explore mais sobre modelagem de bancos de dados e o MySQL Workbench com os links abaixo:

- [MySQL Workbench](https://dev.mysql.com/downloads/workbench/)
- [Documentação do MySQL](https://dev.mysql.com/doc/)
- [Guia de Modelagem de Dados](https://www.lucidchart.com/pages/pt/modelo-entidade-relacionamento)

<p>

🔥 **Pronto para mais?**  
Agora que você completou a modelagem, o próximo passo é implementar o banco de dados ou explorar mais sobre modelagem de dados para expandir seus conhecimentos. Vamos continuar nossa jornada no mundo do desenvolvimento de sistemas! 💥🚀
