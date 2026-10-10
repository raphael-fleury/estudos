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
## 4. Qualidade de dados e gestão de dados mestres e de referência
## 5. Data Lakes e Soluções para Big Data
## 6. Diferenciação entre bancos relacionais, multidimensionais, documentos e grafos
