# 🛒 Projeto Conceitual de Banco de Dados - E-Commerce

## 📖 Sobre o projeto

Este projeto consiste na modelagem conceitual e lógica de um banco de dados para um sistema de **E-Commerce**, desenvolvido como atividade de estudos em modelagem de banco de dados.

O objetivo é representar de forma organizada as principais entidades envolvidas em uma loja virtual, permitindo o gerenciamento de clientes, produtos, fornecedores, pedidos, estoque, vendedores terceiros, pagamentos e entregas.

---

# 📌 Objetivos

- Modelar um banco de dados relacional para um sistema de e-commerce.
- Aplicar conceitos de normalização.
- Utilizar tabelas de relacionamento para resolver relações N:N.
- Tornar o modelo preparado para futuras expansões.

---

# 🗂 Entidades do Projeto

## Cliente

Armazena os dados dos clientes cadastrados na plataforma.

### Atributos

- idCliente
- Nome
- Identificação (CPF ou CNPJ)
- Endereço

---

## Produto

Responsável pelo cadastro dos produtos comercializados.

### Atributos

- idProduto
- Categoria
- Descrição
- Valor

---

## Pedido

Representa uma compra realizada por um cliente.

### Atributos

- idPedido
- Status
- Descrição
- Frete

Relacionamentos:

- Um cliente pode realizar vários pedidos.
- Um pedido possui vários produtos.

---

## Estoque

Representa os locais onde os produtos estão armazenados.

### Atributos

- idEstoque
- Local

---

## Fornecedor

Empresas responsáveis pelo fornecimento dos produtos.

### Atributos

- idFornecedor
- Razão Social
- CNPJ

---

## Vendedor Terceiro

Representa parceiros que vendem produtos através da plataforma.

### Atributos

- idTerceiro
- Razão Social
- Local

---

# 🔗 Tabelas de Relacionamento

## Produto_has_Estoque

Relaciona produtos aos estoques.

Campos:

- Produto_idProduto
- Estoque_idEstoque
- Quantidade

---

## Relação Produto/Pedido

Relaciona os produtos pertencentes a cada pedido.

Campos:

- Produto_idProduto
- Pedido_idPedido
- Quantidade

---

## Disponibilizando Produto

Relaciona fornecedores aos produtos.

Campos:

- Fornecedor_idFornecedor
- Produto_idProduto

---

## Produtos por Vendedor

Relaciona vendedores terceiros aos produtos comercializados.

Campos:

- Terceiro_Vendedor_idTerceiro
- Produto_idProduto
- Quantidade

---

# 🚀 Refinamentos Implementados

## 1️⃣ Cliente PF e PJ

Foi proposta a separação das informações específicas de Pessoa Física e Pessoa Jurídica.

### Estrutura sugerida

```
Cliente
│
├── PessoaFisica
└── PessoaJuridica
```

### Benefícios

- Evita duplicação de dados.
- Um cliente pode ser apenas PF ou PJ.
- Facilita futuras manutenções.

---

## 2️⃣ Pagamentos

Foi adicionada a entidade **Pagamento**, permitindo que um pedido possua mais de uma forma de pagamento.

Exemplo:

Pedido #15

- PIX → R$ 100,00
- Cartão de Crédito → R$ 250,00

### Estrutura

```
Pagamento

idPagamento
Pedido_idPedido
FormaPagamento
Valor
Status
DataPagamento
```

Também pode existir uma tabela auxiliar:

```
FormaPagamento

idForma
Descricao
```

---

## 3️⃣ Entrega

Foi criada uma entidade própria para controlar o envio dos pedidos.

### Estrutura

```
Entrega

idEntrega
Pedido_idPedido
CodigoRastreio
StatusEntrega
Transportadora
DataEnvio
DataEntrega
```

### Benefícios

- Controle do rastreamento.
- Separação das informações logísticas.
- Possibilidade de expansão para múltiplas entregas.

---

# 📊 Relacionamentos

- Cliente → Pedido (1:N)
- Pedido → Produto (N:N)
- Produto → Estoque (N:N)
- Produto → Fornecedor (N:N)
- Produto → Vendedor Terceiro (N:N)
- Pedido → Pagamento (1:N)
- Pedido → Entrega (1:1)

---

# 🧠 Conceitos Aplicados

- Modelo Entidade-Relacionamento (MER)
- Modelo Lógico
- Chaves Primárias (PK)
- Chaves Estrangeiras (FK)
- Relacionamentos 1:1
- Relacionamentos 1:N
- Relacionamentos N:N
- Normalização
- Integridade Referencial

---

# 🛠 Tecnologias Utilizadas

- MySQL Workbench
- Modelo Entidade-Relacionamento (MER)
- Banco de Dados Relacional

---

# 📚 Aprendizados

Durante o desenvolvimento deste projeto foram praticados conceitos importantes de modelagem de banco de dados, como:

- Estruturação de entidades.
- Definição de relacionamentos.
- Criação de tabelas associativas.
- Aplicação de regras de negócio.
- Organização de dados seguindo boas práticas de normalização.

---

# 📷 Diagrama

> Adicione aqui a imagem do diagrama.

```
/images/diagrama-ecommerce.png
```

ou

```md
![Diagrama do Projeto](images/diagrama-ecommerce.png)
```

---

# 👨‍💻 Autor

**Diego Santos**

Estudante de Análise e Desenvolvimento de Sistemas, em transição de carreira para a área de Tecnologia, com foco em Desenvolvimento Back-end, Banco de Dados e Engenharia de Dados.

GitHub: https://github.com/SEU-USUARIO
