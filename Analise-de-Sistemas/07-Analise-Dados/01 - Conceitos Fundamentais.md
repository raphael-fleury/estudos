# Conceitos Fundamentais

## 1. Dado, informação, conhecimento e inteligência

### Dado

- **O que é:** registro bruto e isolado, sem contexto, significado ou interpretação.
- **Exemplo:** `35` ou `28 °C`. Isoladamente, esses valores não dizem o que representam.

### Informação

- **O que é:** dado organizado, estruturado e contextualizado, que ganha significado e responde a perguntas como “o quê?” ou “quem?”.
- **Exemplos:**
  - A idade do cliente José é 35 anos.
  - A temperatura atual em Santos é 28 °C.

### Conhecimento

- **O que é:** integração, análise e interpretação de informações com base em experiência, regras e contexto. Ajuda a compreender o que as informações significam. Pode ser tácito (vivência prática) ou explícito (teoria documentada).
- **Exemplo:** com base no histórico dos últimos anos, temperaturas de 28 °C associadas à alta umidade nesta região indicam grande probabilidade de chuva no fim da tarde.

### Inteligência

- **O que é:** aplicação prática do conhecimento para resolver problemas, adaptar-se a novas situações e tomar decisões estratégicas e eficazes.
- **Exemplo:** decidir antecipar a saída do trabalho ou levar um guarda-chuva para evitar o transtorno de se molhar na tempestade prevista.

## 2. Dados estruturados e dados não estruturados

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

## 3. Conceitos, fundamentos, características, técnicas e métodos de business intelligence (BI)

### Conceito e fundamentos

- **Definição:** Business Intelligence (BI) é a prática de usar dados para compreender a situação da empresa, substituir a intuição (“achismos”) por fatos e orientar o planejamento estratégico. Não se resume a gráficos ou softwares.
- **Origem da informação:** o BI integra dados de sistemas transacionais (OLTP, *Online Transaction Processing*), voltados às operações do dia a dia — como emitir notas ou registrar vendas —, e sistemas analíticos (OLAP, *Online Analytical Processing*), voltados à consulta e consolidação de dados históricos.
- **As quatro perguntas do BI:**
  1. **Descritiva:** o que aconteceu?
  2. **Diagnóstica:** por que aconteceu?
  3. **Preditiva:** o que pode acontecer?
  4. **Prescritiva:** o que deve ser feito a respeito?

### Características principais

- **Consolidação de múltiplas fontes:** reúne dados de ERPs, CRMs, planilhas, bancos de dados, redes sociais e dispositivos IoT.
- **Visão histórica e contextual:** preserva históricos de longo prazo que os sistemas operacionais podem descartar ou compactar.
- **Democratização e autoatendimento (*Self-Service BI*):** permite que gestores e analistas criem filtros e relatórios sem depender exclusivamente da equipe de TI.
- **Interatividade:** oferece painéis dinâmicos com filtros cruzados e detalhamento de indicadores gerais até registros individuais (*drill-down*).

### Arquitetura e componentes

A infraestrutura clássica de BI é composta por etapas sequenciais:

1. **Fontes de dados:** bancos de dados transacionais, arquivos, APIs e *Data Lakes*.
2. **ETL (*Extract, Transform, Load* — extração, transformação e carga):**
   - **Extração:** coleta dados das fontes originais.
   - **Transformação:** limpa ruídos, corrige inconsistências, padroniza formatos e agrega informações.
   - **Carga:** insere os dados tratados no repositório de destino.
3. **Data Warehouse (DW) e Data Marts:**
   - **Data Warehouse:** repositório centralizado que armazena o histórico corporativo consolidado.
   - **Data Marts:** subconjuntos do Data Warehouse voltados a áreas específicas da empresa, como vendas ou recursos humanos.
4. **Modelagem dimensional:** organiza os dados em tabelas de fatos, com métricas numéricas (por exemplo, valor da venda), e tabelas de dimensão, com contextos (por exemplo, cliente, data e produto). Essas estruturas são frequentemente representadas pelos modelos *Star Schema* ou *Snowflake*.
5. **Ferramentas de apresentação e OLAP:** camada de acesso e análise que inclui cubos OLAP, painéis visuais (*dashboards*) e relatórios.

### Técnicas utilizadas

- **Mineração de dados (*Data Mining*):** aplicação de algoritmos e métodos estatísticos para descobrir padrões, correlações ou comportamentos em grandes volumes de dados.
- **OLAP (*Online Analytical Processing*):** análise dos dados em múltiplas dimensões, como consultar vendas por região, trimestre e linha de produto.
- **Benchmarking e KPIs:** comparação de indicadores-chave de desempenho (*Key Performance Indicators*) com metas internas ou referências de mercado.
- **Visualização de dados:** aplicação de boas práticas de design e percepção visual para tornar dados complexos mais fáceis de interpretar, usando gráficos de barras, dispersão e mapas de calor, entre outros.

### Principais ferramentas do mercado

- **Microsoft Power BI:** forte integração com o ecossistema corporativo e custo relativamente baixo.
- **Tableau:** recursos visuais avançados e ampla capacidade de exploração de dados.
- **Qlik Sense:** conhecido pelo motor associativo de dados.
- **Google Looker Studio / Looker:** foco em integrações na nuvem e no ecossistema Google.

## 4. Mapeamento de fontes de dados

O mapeamento de fontes de dados identifica onde estão os dados relevantes para uma análise, como são produzidos e de que forma podem ser acessados. É uma etapa importante para integrar informações confiáveis em soluções de BI.

### Objetivos

- Conhecer os sistemas e responsáveis pelos dados da organização.
- Identificar dados relevantes, duplicados ou inexistentes para cada necessidade de negócio.
- Avaliar a qualidade, a disponibilidade e as limitações de uso das fontes.
- Planejar a integração dos dados e manter sua origem rastreável (*data lineage*).

### Classificação das fontes

- **Origem:** internas (ERP, CRM, sistemas financeiros e planilhas corporativas) ou externas (dados públicos, fornecedores, redes sociais e serviços de mercado).
- **Formato:** estruturadas (tabelas relacionais), semiestruturadas (JSON, XML e logs) ou não estruturadas (documentos, imagens, áudio e vídeo).
- **Forma de acesso:** bancos de dados, arquivos, APIs, aplicações em nuvem ou dispositivos IoT.
- **Frequência de atualização:** tempo real, periódica ou sob demanda.

### Informações a registrar

Para cada fonte, documente:

- nome e descrição do sistema ou conjunto de dados;
- área responsável e pessoa de contato;
- entidades, tabelas ou arquivos disponíveis e seus principais campos;
- significado dos campos, formatos, unidades e granularidade dos registros;
- localização, método de acesso e frequência de atualização;
- período histórico disponível e volume aproximado;
- qualidade conhecida, como campos ausentes, duplicidades e inconsistências;
- regras de acesso, classificação de confidencialidade e restrições legais;
- dependências, transformações realizadas e destino dos dados integrados.

### Etapas do mapeamento

1. **Definir a necessidade de negócio:** esclarecer quais perguntas, indicadores ou decisões serão apoiados.
2. **Identificar fontes candidatas:** consultar áreas de negócio, equipes de TI, catálogos de dados e documentação dos sistemas.
3. **Levantar e descrever os dados:** registrar estruturas, campos, significados, formatos, responsáveis e formas de acesso.
4. **Avaliar adequação e qualidade:** verificar se os dados são completos, consistentes, atuais e detalhados o suficiente para a análise.
5. **Verificar acesso e conformidade:** confirmar autorizações, segurança e requisitos legais, incluindo a LGPD quando houver dados pessoais.
6. **Documentar relações e fluxos:** indicar como os dados se conectam, são transformados e chegam ao Data Warehouse, Data Mart ou ferramenta analítica.
7. **Validar com os responsáveis:** confirmar definições e regras de negócio com as áreas que produzem ou utilizam os dados.

### Exemplo de inventário

| Fonte | Dados disponíveis | Responsável | Atualização | Observações |
|---|---|---|---|---|
| ERP | Pedidos, produtos e faturamento | Operações | Diária | Fonte oficial de vendas |
| CRM | Clientes e oportunidades | Comercial | Horária | Contém dados pessoais; acesso restrito |
| Planilha de metas | Metas mensais por equipe | Gestão comercial | Mensal | Validar versão e responsável antes da carga |

O inventário deve ser mantido atualizado: mudanças nos sistemas, nas regras de negócio ou nos responsáveis podem afetar a confiabilidade dos relatórios e indicadores.
