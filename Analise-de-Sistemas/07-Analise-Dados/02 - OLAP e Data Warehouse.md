# OLAP e Data Warehouse

## 1. Dados estruturados e dados não estruturados

Dados podem ser classificados conforme o grau de organização e a existência de um esquema que defina sua estrutura. Essa classificação influencia como são armazenados, processados e analisados.

### Dados estruturados

- **O que são:** dados organizados segundo um esquema predefinido, com campos, tipos e relações claramente definidos.
- **Onde são encontrados:** principalmente em bancos de dados relacionais, planilhas e sistemas transacionais.
- **Exemplos:** cadastro de clientes (identificador, nome e endereço), pedidos (data, cliente e valor) e registros de estoque.
- **Características:** seguem formatos consistentes, podem ser organizados em linhas e colunas e são consultados com facilidade por linguagens como SQL.
- **Análise:** são adequados a consultas, agregações e análises multidimensionais em estruturas como tabelas de fatos e dimensões de um Data Warehouse.

### Dados semiestruturados

- **O que são:** dados que não seguem necessariamente um esquema tabular rígido, mas contêm marcadores, chaves ou metadados que ajudam a identificar e organizar seus elementos.
- **Exemplos:** documentos JSON e XML, e-mails, logs de aplicações e dados de APIs.
- **Características:** a estrutura pode variar entre registros; novos campos podem ser incluídos sem alterar previamente uma tabela fixa.
- **Análise:** podem exigir validação, padronização e transformação para serem integrados a um Data Warehouse ou usados em consultas analíticas.

### Dados não estruturados

- **O que são:** dados sem uma organização tabular ou um esquema predefinido que descreva diretamente seu conteúdo.
- **Exemplos:** textos livres, documentos, imagens, áudios, vídeos e publicações em redes sociais.
- **Características:** podem conter informação valiosa, mas seu conteúdo não costuma ser consultado diretamente com SQL tradicional. A interpretação pode exigir processamento de linguagem natural, reconhecimento de imagens ou outras técnicas especializadas.
- **Análise:** normalmente requer extração de características, classificação ou conversão para uma representação que possa ser combinada com dados estruturados.

### Comparação

| Tipo | Organização | Exemplos | Tratamento comum |
| --- | --- | --- | --- |
| Estruturado | Esquema rígido, frequentemente em linhas e colunas | Tabelas relacionais, planilhas | SQL, filtros e agregações |
| Semiestruturado | Marcadores ou metadados, com esquema flexível | JSON, XML, logs | Análise da estrutura e transformação |
| Não estruturado | Sem esquema tabular predefinido | Texto livre, imagem, áudio e vídeo | Extração e processamento especializado |

Na prática, uma solução analítica pode integrar as três categorias. Por exemplo, uma análise de vendas pode combinar registros estruturados de pedidos com logs semiestruturados de navegação e comentários não estruturados de clientes. Antes da análise, é importante avaliar a qualidade, o formato, a origem e o significado dos dados e transformá-los conforme os requisitos do destino.

## 2. Conceitos de OLAP e suas operações
## 3. Conceitos de data warehouse
## 4. Técnicas de modelagem e otimização de bases de dados multidimensionais
