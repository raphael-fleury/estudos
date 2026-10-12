# Soluções Avançadas

## 1. Bancos de dados NoSQL

Um banco de dados NoSQL (frequentemente traduzido como "não apenas SQL") são sistemas de gerenciamento de dados não relacionais, projetados para lidar com alto volume, grande variedade e alta velocidade de dados (Big Data).

### Tipos de Bancos de Dados NoSQL
- **Chave-Valor:** Guarda os dados em pares simples de chave e valor (exemplo: Redis, Amazon DynamoDB).
- **Orientado a Documentos:** Armazena dados em formatos estruturados como JSON, BSON ou XML (exemplo: MongoDB, CouchDB).
- **Colunar (Colunas Largas):** Organiza os dados em famílias de colunas em vez de linhas tradicionais, ideal para grandes volumes analíticos (exemplo: Apache Cassandra, HBase).
- **Orientado a Grafos:** Focado em conexões, nós e relacionamentos complexos, como redes sociais (exemplo: Neo4j).

## 2. Integração dos dados (ETL, Transferência de Arquivos e Integração via Base de Dados)

A integração de dados unifica informações de várias fontes para análise, relatórios e suporte à decisão. Os principais métodos — ETL, Transferência de Arquivos e Integração via Base de Dados — funcionam de formas diferentes conforme a necessidade de velocidade, volume e tratamento

### ETL (Extração, Transformação e Carga)

O ETL é um processo estruturado que prepara os dados antes de guardá-los no destino final.
- **Extração (Extract):** Coleta dados brutos de várias fontes (bancos de dados, APIs, planilhas, sistemas legados ou nuvem).
- **Transformação (Transform):** Limpa, remove duplicadas, corrige erros, padroniza formatos (como datas) e aplica regras de negócio.
- **Carga (Load):** Envia os dados já tratados para um repositório central, como um Data Warehouse ou Data Lake.
- **Destaque (ETL vs. ELT):** No ETL tradicional, os dados são transformados antes de entrar no destino. No ELT (muito usado em nuvem), os dados brutos são carregados primeiro e transformados depois, usando o poder de processamento do próprio sistema de destino.
- **Exemplos de ferramentas:** AWS Glue, Databricks, Pentaho e Talend


### Transferência de Arquivos

Consiste na movimentação direta de arquivos fechados (como .csv, .json, .xml, .xlsx ou arquivos de texto delimitados) entre sistemas.

- **Como funciona:** Um sistema gera um arquivo periódico (por exemplo, um fechamento de caixa diário) e o envia para outro local.
- **Mecanismos comuns:** Protocolos como FTP, SFTP, FTPS, ou automações via diretórios compartilhados e bucket na nuvem (ex: Amazon S3).
- **Vantagens:** Simples de implementar, baixo custo e ótimo para integrações legadas ou lotes esporádicos.
- **Desvantagens:** Pouco controle em tempo real, risco de perda ou corrupção de arquivos e dificuldade para rastrear erros linha a linha.

### Integração via Base de Dados

Ocorre de forma direta entre bancos de dados relacionais ou NoSQL, sem a necessidade de gerar arquivos intermediários ou passar por motores pesados de ETL.

#### Como funciona:
- **Conexão Direta / Querys:** Um sistema consulta as tabelas de outro via comandos SQL ou views.
- **Replicação / CDC (Change Data Capture):** O banco de origem captura alterações (inserts, updates, deletes) em tempo real ou quase real e replica no banco de destino.
- **Linked Servers / Stored Procedures:** Banco conversando diretamente com banco por meio de links de rede internos.

## 3. Banco de dados em memória

Um banco de dados em memória (ou in-memory database) é um sistema de gerenciamento de dados que guarda todas as informações diretamente na memória RAM do computador, em vez de usar discos rígidos ou SSDs.

### Principais Características

- **Velocidade extrema:** Elimina a latência de leitura e escrita em discos, permitindo respostas em microssegundos.
- **Menor uso de CPU:** Exige menos instruções do processador para recuperar as informações.
- **Volatilidade e Persistência:** Como a RAM é volátil (perde os dados ao desligar), muitos sistemas usam mecanismos de backup em disco ou replicação para evitar a perda de informações.

### Exemplos Populares

- **Redis:** Muito usado como cache e armazenamento de estruturas em memória.
- **Dragonfly:** Alternativa moderna de alto desempenho ao Redis.
- **Memgraph:** Focado em processamento de dados em formato de grafos em tempo real.
- **SQLite (modo em memória):** Utilizado frequentemente para testes rápidos ou dados temporários.

Não deve ser utilizado quando o volume de dados for maior do que a RAM disponível ou quando os dados não possam ser perdidos em caso de queda de energia, reinicialização ou falha no servidor. É usado com frequência para cache ou bancos de teste.

## 4. Qualidade de dados e gestão de dados mestres e de referência
## 5. Data Lakes e Soluções para Big Data

Um **data lake** é um repositório centralizado que armazena grandes volumes de dados brutos em seu formato nativo. Pode receber dados estruturados, semiestruturados ou não estruturados, sem exigir que um esquema seja definido antes da gravação.

### Principais características

- **Schema-on-read:** a estrutura é aplicada quando os dados são lidos e analisados, e não necessariamente quando são gravados.
- **Baixo custo e alta escalabilidade:** costuma utilizar armazenamento de objetos em nuvem ou infraestruturas distribuídas, permitindo lidar com grandes volumes de dados.
- **Flexibilidade:** pode armazenar arquivos de texto, JSON e logs, além de vídeos, áudios e dados de sensores de Internet das Coisas (IoT).
- **Governança como requisito:** sem catalogação, controle de acesso e regras de qualidade, o repositório pode se tornar um *data swamp* — um conjunto desorganizado de dados cuja origem e confiabilidade são difíceis de determinar.

### Soluções e tecnologias de destaque

#### Armazenamento em nuvem

- **Amazon S3**, na AWS.
- **Google Cloud Storage**, no Google Cloud Platform (GCP).
- **Azure Blob Storage** e **Azure Data Lake Storage**, na Microsoft Azure.

#### Processamento, ingestão e orquestração

- **Apache Spark** e **Apache Hadoop:** processamento distribuído de grandes volumes de dados.
- **Apache Kafka:** ingestão e transmissão de dados em tempo real.
- **Apache Airflow:** orquestração e acompanhamento de pipelines de dados.

#### Plataformas integradas e lakehouse

- **Databricks:** plataforma que combina recursos de data lake com transações ACID por meio do Delta Lake.
- **Cloudian:** solução corporativa de armazenamento de dados em data lakes.
- **Data Lake do Ministério da Justiça e Segurança Pública:** iniciativa pública para integração e análise de dados relacionados à segurança pública.

## 6. Diferenciação entre bancos relacionais, multidimensionais, documentos e grafos

### Bancos de Dados Relacionais

- **Estrutura:** Organizados em tabelas (linhas e colunas), com esquemas rígidos e definidos (DDL).
- **Relacionamentos:** Feitos através de chaves primárias e estrangeiras (Foreign Keys), combinando dados entre tabelas por meio de operações de JOIN.
- **Linguagem:** SQL (Structured Query Language).
- **Propriedades:** Foco forte em transações ACID (Atomicidade, Consistência, Isolamento, Durabilidade), ideais para integridade de dados.
- **Casos de uso:** Sistemas bancários, ERPs, e-commerces e transações financeiras.
- **Exemplos:** PostgreSQL, MySQL, Oracle, SQL Server.

### Bancos de Dados Multidimensionais

- Estrutura: Organizados conceitualmente em cubos de dados (com três ou mais dimensões: X, Y, Z), otimizados para visualização sob múltiplos ângulos de análise.
- Relacionamentos: Baseados em tabelas fato (métricas numéricas) e tabelas dimensão (contextos como tempo, produto, local) — comumente modelados em Star Schema (esquema estrela).
- Foco: Voltados para OLAP (Online Analytical Processing), Business Intelligence (BI) e Data Warehouses.
- Características: Excelente desempenho em agregações complexas e consultas analíticas rápidas, mas com estrutura rígida de cubo (difícil de alterar após construída).
- Exemplos: Microsoft SSAS (SQL Server Analysis Services), Oracle Essbase, IBM Planning Analytics (TM1).

### Bancos de Dados de Documentos (NoSQL)

- **Estrutura:** Armazenam dados em formatos semiestruturados como JSON, BSON ou XML, dispensando um esquema fixo (schema-less / esquema flexível).
- **Relacionamentos:** Em vez de usar joins pesados, costumam aninhar dados relacionados (por exemplo, guardar um vetor de pedidos dentro do documento de um cliente).
- **Foco:** Escalabilidade horizontal facilitada e alta velocidade de leitura/gravação para formatos flexíveis.
- **Casos de uso:** Catálogos de produtos, gestão de conteúdo (CMS), perfis de usuários e APIs modernas.
- **Exemplos:** MongoDB, Couchbase, Amazon DocumentDB.

### Bancos de Dados de Grafos (NoSQL)

- **Estrutura:** Baseados na teoria matemática dos grafos, utilizando nós (entidades como pessoas, contas ou produtos) e arestas (relações que conectam os nós).
- **Relacionamentos:** Armazenados explicitamente e de forma nativa junto ao dado (o relacionamento é um objeto de primeira classe, não exigindo reconstrução via joins em tempo de consulta).
- **Foco:** Consultas profundas e recursivas de conexões (ex: "amigos de amigos de amigos").
- **Casos de uso:** Redes sociais, sistemas de recomendação, detecção de fraudes e grafos de conhecimento.
- **Exemplos:** Neo4j, Amazon Neptune, ArangoDB (multimodelo).
