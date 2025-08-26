---

# 📊 Modelagem de Dados

Pode ser aplicada em demandas de negócio no dia a dia ou usada para aprimorar habilidades em **Data & Analytics**.
Independentemente do objetivo, é essencial entender de **modelagem de dados**.

---

## 🔹 O que é modelagem de dados?

É o processo de **estruturar e organizar dados** para refletir de maneira eficaz as necessidades de um negócio ou aplicação.

---

## 🔹 Por que a modelagem de dados é útil no trabalho?

A modelagem de dados **transforma necessidades de negócio em uma base estruturada**, pronta para suportar decisões e análises realizadas diariamente.

---

## 🔹 Benefícios da modelagem de dados

1. **Clareza e consistência**
   → Ajuda a padronizar e manter consistência nos dados.

2. **Eficiência no desenvolvimento**
   → Um modelo bem definido reduz tempo de desenvolvimento e retrabalho.

3. **Facilidade de escalabilidade e manutenção**
   → Um bom modelo facilita futuras expansões e adaptações no sistema.

---

## 🔹 Riscos da ausência de modelagem de dados

* **Inconsistência e redundâncias** → Geração de dados duplicados, inconsistentes e imprecisos.
* **Dificuldade em manter qualidade dos dados** → Maior esforço para validar e corrigir informações.
* **Aumento de custos e tempo de desenvolvimento** → Impacto no prazo e no custo para ajustar erros de estruturação.

---

## 🔹 Boas práticas

* Entender as necessidades do negócio.
* Mapear fontes e estruturas de dados.
* Definir o **modelo conceitual** antes de partir para o físico.

---

## 🔹 Tipos de modelagem de dados

### 1. **Modelo Conceitual**

* Visão macro, compreensível para todos.
* Mostra **entidades** e **relacionamentos** de forma simples.

```
[Cliente] ---faz---> [Pedido] ---contém---> [Produto]
```

---

### 2. **Modelo Lógico**

* Mais técnico, mas ainda **independente do SGBD**.
* Define atributos, PK, FK, cardinalidades e tipos de dados genéricos.
* Sim, em modelagem lógica, **podemos tratar entidades como tabelas**.

```
Cliente (id_cliente PK, nome, telefone, email)  
Pedido (id_pedido PK, data, valor_total, id_cliente FK)  
Produto (id_produto PK, nome, preco)
```

---

### 3. **Modelo Lógico Relacional**

* Refinamento do lógico, mas já pensando em SQL (relacional).
* Define tabelas, colunas e relacionamentos estruturados.

---

### 4. **Modelo Lógico NoSQL (não relacional)**

* Estrutura pensada para bancos NoSQL (documentos, grafos, chave-valor, colunar).
* Exemplo em MongoDB: documentos JSON com subestruturas.

---

### 5. **Modelo Lógico Dimensional**

* Usado em Data Warehouse / BI.
* Divide em **tabela fato** (eventos, métricas) e **tabelas dimensão** (atributos de análise).

```
FatoVendas (quantidade, valor_total, id_cliente, id_produto, id_tempo)  
DimCliente (nome, cidade, estado)  
DimProduto (nome, categoria, preco)  
DimTempo (data, ano, mês, dia)
```

---

### 6. **Modelo Físico**

* Implementação real em um SGBD específico.
* Usa sintaxe e tipos de dados próprios de cada tecnologia.

👉 Exemplo em **MySQL**:

```sql
CREATE TABLE Cliente (
   id_cliente INT AUTO_INCREMENT PRIMARY KEY,
   nome VARCHAR(100),
   telefone VARCHAR(20),
   email VARCHAR(100)
);
```

👉 Exemplo em **PostgreSQL**:

```sql
CREATE TABLE Cliente (
   id_cliente SERIAL PRIMARY KEY,
   nome TEXT,
   telefone VARCHAR(20),
   email TEXT
);
```

---

## 🔹 Tabelas fato e dimensão

* **Tabela fato**: armazena medidas do negócio (ex.: vendas, quantidade, valor). É a tabela principal, ligada às dimensões por meio de chaves estrangeiras.
* **Tabelas dimensão**: guardam atributos descritivos (ex.: cliente, produto, tempo, loja).

---

## 🔹 Cardinalidade

Cardinalidade descreve como as entidades se relacionam:

* **1:1 (um para um)** → cada registro de uma tabela se relaciona com no máximo 1 da outra.
  Ex.: Pessoa ↔ CPF.
* **1\:N (um para muitos)** → um registro de uma tabela se relaciona com vários da outra.
  Ex.: Cliente ↔ Pedido.
* **N\:N (muitos para muitos)** → vários registros de uma tabela se relacionam com vários da outra.
  Ex.: Aluno ↔ Disciplina.

---

## ✅ Resumo final

* A **modelagem de dados** é o **passo anterior** à criação física do banco.
* Ela ajuda a **planejar, organizar e estruturar** como os dados vão se relacionar.
* O **modelo lógico é universal**, enquanto o **físico depende do SGBD** escolhido (MySQL, PostgreSQL, Oracle, SQL Server, MongoDB etc.).
* É o que garante **clareza, eficiência e escalabilidade** nos sistemas.

---


