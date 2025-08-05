# Atividade: Explorando Banco de Dados Relacional, Não Relacional e Normalização
![Logo do GitHub](https://media.licdn.com/dms/image/v2/D4D12AQFqhwXZi5hVRA/article-cover_image-shrink_600_2000/article-cover_image-shrink_600_2000/0/1656893698072?e=2147483647&v=beta&t=TUQHsLUNBL6Q-PgM2p3WQhXhR3qUD8i0TbGnj3Edpt8)

## 1. Conceitos Teóricos

### O que é um Banco de Dados Relacional?

Um **banco de dados relacional** organiza os dados em **tabelas** com linhas e colunas, e utiliza **chaves primárias** e **estrangeiras** para estabelecer relacionamentos. A principal linguagem para manipulação é o **SQL**.

**Exemplo de uso**: Um sistema de gestão de vendas, onde os dados de clientes, produtos e vendas são armazenados em tabelas diferentes, mas relacionadas entre si.

---

### O que é um Banco de Dados Não Relacional?

Os **bancos de dados não relacionais (NoSQL)** não usam tabelas, mas sim **documentos**, **chave-valor**, ou **grafos**. Eles oferecem mais flexibilidade e escalabilidade, ideais para grandes volumes de dados ou quando a estrutura de dados não é fixa.

**Exemplo de uso**: Aplicações como redes sociais ou plataformas de e-commerce, onde os dados variam muito e não seguem um formato fixo.

---

### O que é Normalização?

A **normalização** é o processo de organizar os dados para **evitar redundâncias** e garantir a **integridade** do banco de dados. Ela é feita em **formas normais (FN)**, sendo a 1ª, 2ª e 3ª as mais comuns.

**Objetivo**: Garantir que os dados sejam armazenados de forma eficiente, evitando duplicação e erros de consistência.

---

## 2. Exemplo de Tabela Não Normalizada

A tabela abaixo contém informações de pedidos, com dados repetidos e dependências inadequadas.

| Pedido_ID | Cliente_Nome | Cliente_Endereço | Produto_ID | Produto_Nome | Quantidade | Preço_Total |
|-----------|--------------|------------------|------------|--------------|------------|-------------|
| 1         | João Silva   | Rua A, 123       | 10         | Caneta       | 2          | 4,00        |
| 1         | João Silva   | Rua A, 123       | 11         | Lápis        | 1          | 2,00        |
| 2         | Maria Souza  | Av. B, 456       | 10         | Caneta       | 5          | 10,00       |

---

## 3. Normalização até a 3ª Forma Normal (3FN)

### 1ª Forma Normal (1FN)

A 1FN garante que cada célula da tabela contenha **apenas um valor** e que as colunas sejam **atômicas**. A tabela já está na 1FN, mas contém **redundâncias** no nome e endereço do cliente.

---

### 2ª Forma Normal (2FN)

A 2FN remove **dependências parciais**. Isso significa que, se a chave primária for composta (por exemplo, `Pedido_ID` + `Produto_ID`), nenhum atributo deve depender apenas de parte da chave.

Solução: Criar tabelas separadas para **clientes** e **produtos**.

---

### 3ª Forma Normal (3FN)

A 3FN elimina **dependências transitivas**. Isso significa que atributos não-chave não podem depender de outros atributos não-chave.

Solução: Criar quatro tabelas normalizadas.

---

## 4. Tabelas Normalizadas

### Tabela: Clientes

| Cliente_ID | Nome         | Endereço      |
|------------|--------------|---------------|
| 1          | João Silva   | Rua A, 123    |
| 2          | Maria Souza  | Av. B, 456    |

---

### Tabela: Produtos

| Produto_ID | Nome     |
|------------|----------|
| 10         | Caneta   |
| 11         | Lápis    |

---

### Tabela: Pedidos

| Pedido_ID | Cliente_ID |
|-----------|------------|
| 1         | 1          |
| 2         | 2          |

---

### Tabela: Itens_Pedido

| Pedido_ID | Produto_ID | Quantidade | Preço_Total |
|-----------|------------|------------|-------------|
| 1         | 10         | 2          | 4,00        |
| 1         | 11         | 1          | 2,00        |
| 2         | 10         | 5          | 10,00       |

---

## 5. Conclusão

Através do processo de normalização, conseguimos **eliminar redundâncias**, **organizar os dados** de forma mais eficiente e garantir a **integridade e consistência** do banco de dados. Isso facilita a **manutenção** e **escalabilidade** do sistema.

---
#### Daniel Cavalcante Martins - DEV 1B
