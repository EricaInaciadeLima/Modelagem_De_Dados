## 📘 Entidade

**Entidade** é a nomenclatura utilizada ao estruturar uma "tabela" durante a etapa de modelagem do **DER (Diagrama Entidade-Relacionamento)**. Basicamente, um ou mais **objetos** do mundo real transformam-se em entidades no modelo de dados.

Ela representa um **conjunto de objetos** sobre os quais desejamos **armazenar informações** no banco de dados. Cada entidade possui atributos que descrevem suas características e uma chave que permite identificá-la de forma única.



### 🧠 Regras para identificar a necessidade de criação de uma entidade

Ao modelar um sistema, considere criar uma entidade quando:

- Há necessidade de guardar informações sobre cada objeto.
- Existem múltiplos objetos do mesmo tipo.
- Existe uma chave (atributo) capaz de identificar cada objeto de forma única.

### 📌 Exemplo de entidade

Suponha que estamos modelando um sistema de biblioteca. Uma possível entidade seria:

```markdown
Entidade: Livro

Atributos:
- ID_Livro (chave primária)
- Título
- Autor
- Ano_Publicação
- Gênero
```

Neste exemplo:
- Precisamos guardar informações sobre cada livro.
- Há vários livros no acervo.
- Cada livro pode ser identificado de forma única pelo `ID_Livro`.

---

Claro, Erica! Aqui está sua explicação revisada e formatada em **Markdown**, com correções de ortografia, pontuação e fluidez — mantendo seu estilo direto e objetivo:

---

## 🧩 Atributos

**Atributos** são as características que cada **entidade** (na modelagem conceitual) ou **tabela** (na modelagem física, última etapa) possui. Eles representam as **propriedades** dos objetos que queremos armazenar no banco de dados.

Cada atributo define **que tipo de dado será armazenado**, dependendo do tipo de modelagem. Os principais tipos incluem:

- `string` – textos, nomes, descrições
- `number` – valores numéricos, como idade ou quantidade
- `chave primária` – identificador único de cada registro
- `enum` – conjunto limitado de valores pré-definidos (ex: status: "ativo", "inativo")

### 📌 Exemplo

```markdown
Entidade: Produto

Atributos:
- ID_Produto (chave primária, number)
- Nome (string)
- Preço (number)
- Categoria (enum: "Eletrônico", "Vestuário", "Alimento")
```

---

Claro, Erica! Aqui está sua explicação revisada com correções de ortografia, fluidez e formatação em **Markdown**, além de um exemplo para ilustrar cada característica da chave primária:

---

## 🔑 Chave Primária

**Chave Primária (PK – Primary Key)** é um tipo especial de **atributo** que usamos para **identificar de forma única** cada registro dentro de uma **entidade** (na modelagem conceitual) ou **tabela** (na modelagem física).

Geralmente, atribuímos esse papel a um campo chamado `ID`, mas qualquer atributo que cumpra os requisitos pode ser usado como chave primária.

### 📐 Características da Chave Primária

1. **Unicidade**  
   Cada valor da chave primária deve ser único.  
   👉 *Exemplo:* Dois clientes não podem ter o mesmo `ID_Cliente`.

Sim, Erica, você está certíssima em destacar isso — e sua explicação sobre **minimalidade** está muito boa! 👏 Vamos só enriquecer um pouco mais com uma observação importante sobre **chaves compostas**, que também se relaciona com esse princípio.


2.  **Chave Composta e Minimalidade**

Uma **chave composta** é formada por **dois ou mais atributos** que, juntos, garantem a identificação única de um registro. Ela é usada quando **nenhum atributo isolado** consegue cumprir esse papel.

### ✅ Minimalidade aplicada à chave composta

Mesmo em chaves compostas, o princípio da **minimalidade** continua valendo:  
> A chave deve conter **apenas os atributos necessários** para garantir a unicidade. Nada de excesso!

### 🧾 Exemplo prático:

Imagine uma tabela `Matricula` que registra alunos em disciplinas:

| RA_Aluno | Cod_Disciplina | Data_Matricula |
|----------|----------------|----------------|
| 12345    | MAT101         | 2025-08-20     |
| 12345    | FIS102         | 2025-08-21     |

Neste caso, **nenhum dos dois atributos isoladamente** identifica a matrícula de forma única.  
✅ A chave composta `RA_Aluno + Cod_Disciplina` é **mínima e necessária**.  
🚫 Incluir `Data_Matricula` na chave seria **excesso**, violando a minimalidade.




3. **Imutabilidade**  
   O valor da chave primária não deve mudar ao longo do tempo.  
   👉 *Exemplo:* O `ID_Produto` de um item no estoque permanece o mesmo, mesmo que o nome ou preço mudem.

4. **Obrigatoriedade**  
   A chave primária **não pode ser nula**. Todo registro deve ter um valor definido para ela.  
   👉 *Exemplo:* Não pode existir um pedido sem `ID_Pedido`.

---


## 🔗 Chave Estrangeira (FK – Foreign Key)

A **chave estrangeira** é um tipo especial de **atributo** que usamos para **conectar duas entidades** (na modelagem conceitual) ou **duas tabelas** (na modelagem física). Ela representa um **vínculo** com a **chave primária** de outra entidade ou tabela.

Em outras palavras:  
> A chave estrangeira é um atributo que **referencia** a chave primária de outra tabela, permitindo **relacionar os dados** entre elas.

### 🧠 Como funciona

- A chave primária de uma tabela **origem** é usada como chave estrangeira em uma tabela **destino**.
- Isso garante **integridade referencial**: ou seja, os dados estão conectados corretamente e não há registros "órfãos".

---

### 🧾 Exemplo prático

Imagine duas tabelas: `Cliente` e `Pedido`.

```markdown
Tabela: Cliente
- ID_Cliente (PK)
- Nome
- CPF

Tabela: Pedido
- ID_Pedido (PK)
- Data
- Valor
- ID_Cliente (FK)
```

Neste exemplo:
- `ID_Cliente` é a **chave primária** na tabela `Cliente`.
- `ID_Cliente` também aparece na tabela `Pedido`, mas como **chave estrangeira**, indicando **qual cliente fez o pedido**.

---

Você está no caminho certo, Erica! 👏 A ideia de que o **relacionamento** entre entidades é representado por meio de **chaves estrangeiras** está correta. Vamos só lapidar a redação para deixá-la mais clara, técnica e fluida. Aqui vai uma versão revisada com explicação e exemplo:

---

## 🔗 Relacionamento

Um **relacionamento** é a **associação entre duas ou mais entidades** que expressa como elas estão conectadas dentro de um modelo de dados.  
Na modelagem física (banco de dados relacional), essa conexão é implementada por meio de **chaves estrangeiras (Foreign Keys)**.

> A estrutura e o tipo de relacionamento dependem das **regras de negócio** — ou seja, da lógica e das exigências do sistema que está sendo modelado.

---

### 🔄 Tipos de Relacionamento

| Tipo             | Descrição                                                                 |
|------------------|---------------------------------------------------------------------------|
| 1:1 (um para um) | Um registro em uma entidade se relaciona com **um único** registro em outra. |
| 1:N (um para muitos) | Um registro em uma entidade se relaciona com **vários** registros em outra. |
| N:N (muitos para muitos) | Vários registros em uma entidade se relacionam com **vários** registros em outra. Requer uma **tabela associativa**. |

---

### 🧾 Exemplo prático

Imagine duas entidades: `Aluno` e `Curso`.

```markdown
Entidade: Aluno
- ID_Aluno (PK)
- Nome

Entidade: Curso
- ID_Curso (PK)
- Nome_Curso

Relacionamento: Matricula
- ID_Aluno (FK)
- ID_Curso (FK)
- Data_Matricula
```

Neste caso:
- O relacionamento **"Matricula"** conecta `Aluno` e `Curso`.
- Ele é do tipo **N:N**, pois um aluno pode se matricular em vários cursos, e um curso pode ter vários alunos.
- A tabela `Matricula` funciona como **tabela associativa**, contendo as chaves estrangeiras de ambas as entidades.

---
Perfeito, Erica! Agora vamos complementar esse conteúdo com o conceito de **cardinalidade mínima e máxima**, que é essencial para entender **como os relacionamentos funcionam na prática** dentro de um modelo de dados.

---

## 🔢 Cardinalidade Mínima e Máxima

A **cardinalidade** define **quantos registros** de uma entidade podem estar associados a registros de outra entidade em um relacionamento.

Ela é composta por dois aspectos:

### 🔸 Cardinalidade Mínima
Indica o **número mínimo de ocorrências** que uma entidade deve ter no relacionamento.  
- Pode ser **0** (opcional) ou **1** (obrigatório).

### 🔸 Cardinalidade Máxima
Indica o **número máximo de ocorrências** que uma entidade pode ter no relacionamento.  
- Pode ser **1** (um para um) ou **N** (um para muitos ou muitos para muitos).

---

### 🧾 Exemplo com Cardinalidade

Vamos usar o mesmo exemplo de `Aluno`, `Curso` e `Matricula`.

```markdown
Relacionamento: Matricula
Entre: Aluno e Curso
```

| Entidade | Cardinalidade Mínima | Cardinalidade Máxima | Interpretação |
|----------|----------------------|-----------------------|---------------|
| Aluno    | 0                    | N                     | Um aluno pode não estar matriculado (opcional), ou pode estar em vários cursos. |
| Curso    | 1                    | N                     | Um curso deve ter pelo menos um aluno (obrigatório), e pode ter vários. |

---

### 💡 Representação em Diagramas ER

Nos diagramas, a cardinalidade costuma ser representada assim:

- **(0,N)** → zero ou muitos  
- **(1,N)** → um ou muitos  
- **(1,1)** → exatamente um  
- **(0,1)** → opcional, no máximo um

---

