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

A independência de dados é uma propriedade fundamental de um sistema de banco de dados (SGBD) que permite que as alterações em um nível de abstração não afetem os níveis superiores. Existem dois tipos principais de independência de dados:

### Independência lógica

Permite alterar o esquema lógico (como a estrutura dos dados) sem que isso afete as aplicações ou visões externas.

**Exemplo:** Se adicionar uma nova coluna a uma tabela ou dividir uma tabela em duas, as aplicações existentes não devem deixar de funcionar. Apenas a vista que serve essa aplicação precisa de ser ajustada internamente no SGBD.


### Independência física

Permite alterar o esquema físico (como a estrutura de armazenamento) sem afetar o esquema lógico ou as aplicações. 

**Exemplo:** Se decidir mudar a base de dados de um disco rígido tradicional para um SSD, alterar o formato de compressão dos ficheiros ou criar um novo índice para tornar as pesquisas mais rápidas, a estrutura das tabelas e o código das aplicações permanecem exatamente os mesmos.

## 4. Transações de bancos de dados

Uma transação de banco de dados é um conjunto de uma ou mais operações executadas como uma única unidade lógica de trabalho, garantindo que tudo seja concluído com sucesso ou que nenhuma alteração seja aplicada. Devem seguir os 4 princípios ACID citados anteriormente.

## 5. Melhoria de performance de banco de dados

Principais estratégias:

### Otimização de Consultas (SQL Tuning)
- Evitar o uso de `SELECT *` e trazer apenas as colunas realmente necessárias.
- Substituir subconsultas lentas ou `IN` por `EXISTS` quando aplicável.
- Analisar o Plano de Execução (`EXPLAIN PLAN`, `EXPLAIN`, etc.) para entender como o motor do banco lê os dados.

### Indexação Estratégica
- Criar índices nas colunas mais utilizadas em cláusulas `WHERE`, `JOIN` e `ORDER BY`.
- Evitar excesso de índices, pois eles aceleram as leituras, mas tornam operações de escrita (`INSERT`, `UPDATE`, `DELETE`) mais lentas.

### Modelagem e Normalização

Estruturar tabelas de forma equilibrada para evitar redundâncias, ou utilize técnicas controladas de desnormalização quando a leitura precisar ser extremamente rápida.

### Uso de Cache

Armazear em cache resultados de consultas frequentes ou utilize o buffer/cache interno do SGBD para evitar acessos repetidos ao disco.

### Configuração e Monitoramento
- Ajustar parâmetros de memória compartilhada, tamanho de buffers e conexões máximas do servidor.
- Monitorar em tempo real o uso de CPU, disco, I/O e sessões ativas usando ferramentas como o Oracle Database Performance Management ou comandos de sistema.
