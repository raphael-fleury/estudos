# OLAP e Data Warehouse

## 1. Conceitos de OLAP e suas operações

**OLAP** (*Online Analytical Processing*, ou processamento analítico on-line) é uma forma de consultar e analisar grandes volumes de dados por diferentes perspectivas. Em vez de registrar uma venda por vez, como acontece em um sistema operacional, o OLAP ajuda a responder perguntas como: “Quanto vendemos por produto, região e mês?”.

Os dados podem ser entendidos como um cubo:

- **Medidas:** os valores que queremos analisar, como quantidade vendida ou faturamento.
- **Dimensões:** as perspectivas usadas para organizar a análise, como tempo, produto e região. Uma dimensão pode ter níveis: em tempo, por exemplo, dia, mês, trimestre e ano.

As principais operações OLAP são:

- **Drill-down (detalhar):** ir de uma visão resumida para outra mais detalhada. Exemplo: sair do faturamento anual e ver o faturamento por trimestre ou mês.
- **Roll-up (resumir):** fazer o caminho inverso, agrupando dados em um nível mais geral. Exemplo: juntar os meses para obter o total do ano.
- **Slice (fatia):** selecionar um único valor de uma dimensão. Exemplo: analisar apenas as vendas de 2025.
- **Dice (subcubo):** selecionar vários valores ou intervalos em mais de uma dimensão. Exemplo: analisar alguns produtos, em duas regiões, durante o primeiro trimestre.
- **Pivot (rotacionar):** mudar a disposição das dimensões na tabela ou no relatório para comparar os dados por outro ângulo, sem alterar os valores.

Em resumo, essas operações permitem resumir, detalhar, filtrar e reorganizar os dados para facilitar a comparação e a tomada de decisões.

## 2. Conceitos de data warehouse
## 3. Técnicas de modelagem e otimização de bases de dados multidimensionais
