# Linguagem SQL

SQL (Structured Query Language) é a linguagem padrão usada para trabalhar com bancos de dados relacionais. Ela permite consultar, inserir, alterar e excluir dados, além de definir a estrutura do banco.

## 1. Linguagem de consulta estruturada (SQL)
A linguagem SQL, em sua essência, serve para consultar e manipular dados armazenados em tabelas. É a parte mais usada em sistemas de informação, pois permite buscar informações relevantes com rapidez.

### Resumo
- Permite consultar dados com `SELECT`.
- Filtra registros com `WHERE`.
- Ordena resultados com `ORDER BY`.
- Agrupa dados com `GROUP BY`.
- Relaciona tabelas com `JOIN`.

### Exemplo
```sql
SELECT nome, salario
FROM funcionarios
WHERE salario > 5000
ORDER BY nome;
```

Esse comando busca os nomes e salários dos funcionários com salário acima de 5000, ordenando o resultado por nome.

---

## 2. Linguagem de definição de dados (DDL)
A DDL é responsável por definir a estrutura do banco de dados, ou seja, criar, alterar e excluir tabelas, colunas e outros objetos.

### Resumo
- `CREATE` cria objetos.
- `ALTER` modifica objetos existentes.
- `DROP` remove objetos.
- `TRUNCATE` limpa os dados de uma tabela sem apagar a estrutura.

### Exemplo
```sql
CREATE TABLE clientes (
    id INT PRIMARY KEY,
    nome VARCHAR(50),
    email VARCHAR(100) UNIQUE,
    idade INT
);
```

Esse comando cria a tabela `clientes` com colunas para id, nome, email e idade.

```sql
ALTER TABLE clientes
ADD COLUMN telefone VARCHAR(20);
```

Aqui a tabela recebe uma nova coluna chamada `telefone`.

---

## 3. Linguagem de manipulação de dados (DML)
A DML é usada para inserir, alterar, excluir e consultar dados dentro das tabelas já criadas.

### Resumo
- `INSERT` adiciona novos registros.
- `UPDATE` altera registros existentes.
- `DELETE` remove registros.
- `SELECT` consulta dados.

### Exemplo
```sql
INSERT INTO clientes (id, nome, email, idade)
VALUES (1, 'Ana', 'ana@email.com', 28);
```

Esse comando insere um novo cliente na tabela.

```sql
UPDATE clientes
SET idade = 29
WHERE id = 1;
```

Esse comando altera a idade do cliente com `id = 1`.

```sql
DELETE FROM clientes
WHERE id = 1;
```

Esse comando remove o cliente de id 1.

```sql
SELECT * FROM clientes;
```

Esse comando mostra todos os registros da tabela `clientes`.

---

## 4. Linguagem de controle de transações (DTL)
A DTL é responsável por controlar transações no banco de dados, garantindo que operações sejam executadas de forma segura e consistente.

### Resumo
- `BEGIN TRANSACTION` inicia uma transação.
- `COMMIT` confirma as mudanças.
- `ROLLBACK` desfaz as mudanças caso ocorra erro.
- `SAVEPOINT` cria um ponto de retorno intermediário.

### Exemplo
```sql
BEGIN TRANSACTION;

UPDATE contas
SET saldo = saldo - 100
WHERE id = 1;

UPDATE contas
SET saldo = saldo + 100
WHERE id = 2;

COMMIT;
```

Nesse exemplo, uma transferência entre contas é realizada. Se algo falhar, o sistema pode usar `ROLLBACK` para cancelar toda a operação.

```sql
ROLLBACK;
```

Esse comando desfaz todas as alterações da transação atual.

---

## 5. Linguagem de controle de dados (DCL)
A DCL é usada para controlar o acesso e a permissão dos usuários no banco de dados.

### Resumo
- `GRANT` concede permissões.
- `REVOKE` remove permissões.
- `DENY` bloqueia acesso em alguns SGBDs.

### Exemplo
```sql
GRANT SELECT, INSERT ON clientes TO usuario1;
```

Esse comando permite que o usuário `usuario1` consulte e insira dados na tabela `clientes`.

```sql
REVOKE INSERT ON clientes FROM usuario1;
```

Esse comando remove a permissão de inserção do usuário `usuario1`.

---

## Resumo final
- SQL é a linguagem padrão dos bancos relacionais.
- DDL define a estrutura do banco.
- DML manipula os dados armazenados.
- DTL controla transações e integridade das operações.
- DCL gerencia permissões e segurança de acesso.

Exemplo simples de fluxo:
1. Criar tabela com DDL.
2. Inserir dados com DML.
3. Confirmar ou desfazer operações com DTL.
4. Definir quem pode acessar com DCL.

Exemplo completo:
```sql
CREATE TABLE produtos (
    id INT PRIMARY KEY,
    nome VARCHAR(50),
    preco DECIMAL(10,2)
);

INSERT INTO produtos (id, nome, preco)
VALUES (1, 'Teclado', 150.00);

SELECT nome, preco
FROM produtos
WHERE preco > 100;

GRANT SELECT ON produtos TO usuario1;
```

Esse exemplo mostra, de forma prática, como SQL organiza a criação, a inserção, a consulta e o controle de acesso ao banco.
