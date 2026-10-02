# 📊 Análise Exploratória de Vendas com SQLite

## 📌 Sobre o projeto

Este projeto apresenta uma **Análise Exploratória de Dados (EDA)** aplicada a uma base de vendas, utilizando **SQLite e SQL** para investigar o comportamento das vendas, produtos, clientes, pagamentos e entregas.

O objetivo foi realizar uma análise **end-to-end**, passando pela organização dos dados, exploração das informações, criação de métricas e identificação de padrões e oportunidades de negócio.

---

## 🎯 Objetivos

* Analisar o desempenho das vendas;
* Identificar produtos com maior volume de vendas;
* Analisar as formas de pagamento utilizadas;
* Avaliar o status dos pedidos;
* Analisar descontos aplicados;
* Investigar a evolução das vendas ao longo do tempo;
* Explorar a distribuição de clientes por região;
* Analisar informações relacionadas às entregas;
* Transformar os resultados da análise em insights de negócio.

---

## 🗂️ Estrutura dos dados

O projeto utiliza cinco tabelas:

| Tabela         | Descrição                        |
| -------------- | -------------------------------- |
| `DIM_Customer` | Informações dos clientes         |
| `DIM_Delivery` | Informações sobre entregas       |
| `DIM_Products` | Cadastro dos produtos            |
| `DIM_Shopping` | Itens e quantidades compradas    |
| `FACT_Orders`  | Informações dos pedidos e vendas |

### Principais informações disponíveis

**Clientes**

* ID do cliente
* Nome
* Cidade
* Estado
* Região

**Produtos**

* ID do produto
* Nome
* Categoria
* Subcategoria
* Preço

**Pedidos**

* Data do pedido
* Desconto
* Subtotal
* Total
* Forma de pagamento
* Status da compra

**Entregas**

* Serviço utilizado
* Preço do serviço
* Data prevista
* Data de entrega
* Status da entrega

---

## 🛠️ Tecnologias utilizadas

* **SQLite**
* **SQL**
* **DB Browser for SQLite**
* **Git**
* **GitHub**

### Principais recursos SQL utilizados

```text
SELECT
WHERE
GROUP BY
ORDER BY
HAVING
CASE WHEN
COUNT
SUM
AVG
MIN
MAX
Subqueries
CTEs
Window Functions
strftime()
```

---

## 🔎 Processo de análise

O projeto foi desenvolvido seguindo as seguintes etapas:

```text
Dados brutos
     ↓
Importação para SQLite
     ↓
Conhecimento das tabelas
     ↓
Validação dos dados
     ↓
Análise exploratória
     ↓
Criação de métricas
     ↓
Análise de produtos
     ↓
Análise de clientes
     ↓
Análise de pagamentos
     ↓
Análise de entregas
     ↓
Identificação de padrões
     ↓
Insights de negócio
```

---

## 📈 Análises realizadas

### 💰 Análise de vendas

Foram analisados indicadores como:

* Faturamento total;
* Ticket médio;
* Maior venda;
* Menor venda;
* Subtotal;
* Total após descontos;
* Desconto médio.

Exemplo:

```sql
SELECT
    SUM(Total) AS faturamento_total,
    AVG(Total) AS ticket_medio,
    MAX(Total) AS maior_venda,
    MIN(Total) AS menor_venda
FROM FACT_Orders;
```

---

### 💳 Formas de pagamento

Foi analisada a quantidade de pedidos e o faturamento por método de pagamento.

```sql
SELECT
    payment,
    COUNT(*) AS quantidade_pedidos,
    SUM(Total) AS faturamento
FROM FACT_Orders
GROUP BY payment
ORDER BY faturamento DESC;
```

---

### 📦 Análise de produtos

Foram analisados os produtos considerando quantidade vendida e valor movimentado.

```sql
SELECT
    Product,
    SUM(Quantity) AS quantidade_vendida,
    SUM(Quantity * Price) AS valor_produtos
FROM DIM_Shopping
GROUP BY Product
ORDER BY valor_produtos DESC;
```

---

### 📅 Evolução das vendas

A evolução mensal das vendas foi analisada utilizando `strftime()` do SQLite.

```sql
SELECT
    strftime('%Y-%m', Order_Date) AS mes,
    COUNT(*) AS pedidos,
    SUM(Total) AS faturamento
FROM FACT_Orders
GROUP BY strftime('%Y-%m', Order_Date)
ORDER BY mes;
```

Essa análise permite identificar períodos de maior e menor movimentação.

---

### 📋 Status dos pedidos

Também foi analisada a distribuição dos pedidos entre os diferentes status:

* Confirmado;
* Processando;
* Em Análise;
* Cancelado.

```sql
SELECT
    Purchase_Status,
    COUNT(*) AS quantidade,
    SUM(Total) AS faturamento
FROM FACT_Orders
GROUP BY Purchase_Status
ORDER BY quantidade DESC;
```

---

### 🚚 Análise de entregas

A tabela `DIM_Delivery` foi utilizada para analisar:

* Serviços de entrega;
* Status das entregas;
* Datas previstas;
* Datas realizadas;
* Valores dos serviços.

---

## 💡 Insights

A análise exploratória foi utilizada para transformar os dados em informações relevantes para o negócio.

Entre os principais pontos investigados estão:

* Quais produtos apresentam maior volume de vendas;
* Quais produtos geram maior movimentação financeira;
* Quais métodos de pagamento são mais utilizados;
* Qual é a distribuição dos pedidos por status;
* Qual é o comportamento das vendas ao longo dos meses;
* Como os descontos impactam o valor das vendas;
* Como os clientes estão distribuídos geograficamente;
* Quais serviços e status de entrega apresentam maior ocorrência.

> Os insights quantitativos finais são baseados nos resultados das consultas executadas durante a análise.

---

## 📁 Estrutura do projeto

```text
analise-exploratoria-vendas/
│
├── data/
│   ├── raw/
│   └── database/
│
├── sql/
│   ├── 01_exploracao.sql
│   ├── 02_vendas.sql
│   ├── 03_produtos.sql
│   ├── 04_clientes.sql
│   ├── 05_pagamentos.sql
│   ├── 06_entregas.sql
│   └── 07_insights.sql
│
├── screenshots/
│
└── README.md
```

---

## 🚀 Próximos passos

Como evolução do projeto, podem ser adicionadas:

* Análises utilizando **CTEs**;
* **Window Functions**;
* Ranking de produtos;
* Crescimento percentual mensal;
* Análise acumulada de vendas;
* Análise de Pareto;
* Dashboard para visualização dos resultados;
* Integração com Python e Pandas;
* Automatização do processo de análise.

---

## 👨‍💻 Autor

**Alison Anjos**

Estudante de **Sistemas de Informação**, com foco em **Análise de Dados, Engenharia de Dados e Tecnologia**.

### Tecnologias e conhecimentos

`SQL` · `Python` · `Pandas` · `Apache Spark` · `PySpark` · `Excel` · `ETL` · `Git/GitHub`

🔗 GitHub: [Alisonjda](https://github.com/Alisonjda)

---

⭐ Se este projeto foi útil ou interessante, considere deixar uma estrela no repositório!
