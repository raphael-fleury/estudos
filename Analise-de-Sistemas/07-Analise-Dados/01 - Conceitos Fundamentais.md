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

## 2. Conceitos, fundamentos, características, técnicas e métodos de business intelligence (BI)

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

## 3. Mapeamento de fontes de dados
