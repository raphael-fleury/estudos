# SGBD e Propriedades

## 1. Sistema Gerenciador de Banco de Dados (SGBD)

 Software que serve como intermediário entre os dados armazenados e os aplicativos ou usuários, permitindo criar, organizar, proteger e manipular bases de dados de forma eficiente.

Exemplos populares:
- **Relacionais (SQL)**: MySQL, PostgreSQL, Oracle Database, Microsoft SQL Server e SQLite.
- **Não relacionais (NoSQL)**: MongoDB, Redis e Cassandra.

## 2. Propriedades de banco de dados: atomicidade, consistência, isolamento e durabilidade (ACID)

- **Atomicidade**: a transação acontece por inteiro ou não acontece. Se uma parte falhar, o sistema desfaz todas as alterações anteriores (chamado de _rollback_), evitando dados incompletos.
- **Consistência:** O banco de dados passa de um estado válido para outro válido. Todas as regras, restrições e relações dos dados devem ser respeitadas antes e depois da transação
- **Isolamento:** Várias transações podem ocorrer ao mesmo tempo sem que uma atrapalhe a outra. O resultado de executar operações juntas deve ser o mesmo que executá-las separadamente.
- **Durabilidade:** Quando uma transação é confirmada (o chamado _commit_), os dados ficam salvos de forma permanente. Eles não se perdem nem mesmo se houver uma falha de energia ou queda no sistema.

## 3. Independência de dados
## 4. Transações de bancos de dados
## 5. Melhoria de performance de banco de dados
