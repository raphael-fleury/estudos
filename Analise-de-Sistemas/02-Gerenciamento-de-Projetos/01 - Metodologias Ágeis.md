# Metodologias Ágeis

## 1. Scrum

O **Scrum** é um framework (estrutura) ágil de gerenciamento de projetos criado nos anos 1990 por Ken Schwaber e Jeff Sutherland. Seu foco é entregar valor de forma iterativa e incremental.

### Pilares fundamentais

- **Transparência:** todos os envolvidos têm visibilidade clara do trabalho e do processo.
- **Inspeção:** o progresso e os artefatos são avaliados com frequência para detectar desvios.
- **Adaptação:** o plano ou o produto é ajustado rapidamente quando a inspeção mostra que uma mudança é necessária.

### Papéis e responsabilidades

- **Product Owner (Proprietário do Produto):** define o que deve ser feito, gerencia e prioriza o *Product Backlog* (lista de pendências).
- **Scrum Master:** facilita o processo, remove impedimentos e ajuda o time a seguir as práticas do Scrum.
- **Time de Desenvolvimento:** equipe multifuncional, geralmente com cerca de 3 a 10 pessoas, responsável por criar o incremento do produto.

### Ciclo e eventos

- **Sprint:** ciclo de trabalho curto e fixo, geralmente de 1 a 4 semanas, no qual um incremento utilizável é construído.
- **Planejamento da Sprint (*Sprint Planning*):** reunião inicial para definir o objetivo e selecionar o trabalho do ciclo.
- **Scrum Diário (*Daily Scrum*):** reunião rápida, de até 15 minutos, para alinhar o trabalho do dia.
- **Revisão da Sprint (*Sprint Review*):** apresentação do trabalho concluído aos interessados (*stakeholders*).
- **Retrospectiva da Sprint:** momento para a equipe avaliar seu processo de trabalho e planejar melhorias.

### Artefatos

- **Product Backlog:** lista priorizada de funcionalidades, requisitos e demais itens desejados para o produto.
- **Sprint Backlog:** itens do *Product Backlog* selecionados para a Sprint atual, junto ao plano para realizá-los.
- **Incremento:** resultado tangível e utilizável produzido ao longo da Sprint.

## 2. Kanban

O **Kanban** é um método visual de gerenciamento de fluxo de trabalho, criado na Toyota por Taiichi Ohno na década de 1940 e posteriormente adaptado para equipes modernas por David J. Anderson.

### Como funciona

- **Quadro visual:** as tarefas são representadas por cartões, físicos ou digitais, e organizadas em colunas que indicam as etapas do processo, como *A Fazer*, *Em Andamento* e *Concluído*.
- **Sistema puxado (*pull*):** novas tarefas entram no fluxo conforme a equipe tem capacidade para executá-las, evitando o acúmulo de trabalho.
- **Limite de WIP (*Work in Progress*):** define o número máximo de tarefas que podem ser realizadas ao mesmo tempo, ajudando a manter o foco e evitar gargalos.
- **Fluxo contínuo:** ao contrário de métodos organizados em ciclos fechados, como o Scrum, o Kanban permite priorizar e adicionar demandas conforme elas surgem.

## 3. Gestão de projeto

A **gestão de projetos** é a aplicação de conhecimentos, habilidades, ferramentas e técnicas para planejar, executar, monitorar e concluir um conjunto de atividades com início e fim definidos. Seu objetivo é alcançar metas respeitando restrições de tempo, custo e escopo.

### Grupos de processos principais

- **Iniciação:** definição dos objetivos e da viabilidade do projeto, além da identificação das partes interessadas (*stakeholders*).
- **Planejamento:** detalhamento do cronograma, orçamento, escopo, recursos e riscos.
- **Execução:** realização das tarefas planejadas para produzir as entregas do projeto.
- **Monitoramento e controle:** acompanhamento do desempenho e aplicação de ajustes quando necessário para corrigir desvios.
- **Encerramento:** entrega final aos *stakeholders*, avaliação dos resultados e fechamento formal do projeto.

### Elementos fundamentais

- **Escopo:** o que será entregue pelo projeto.
- **Cronograma:** duração e sequência das etapas de execução.
- **Recursos:** custos, materiais e equipe envolvidos.

### Abordagens e metodologias

- **Tradicional ou preditiva (cascata ou *waterfall*):** escopo definido e planejamento detalhado desde o início.
- **Ágil (Scrum ou Kanban):** entregas em ciclos curtos, com maior flexibilidade para incorporar mudanças.
- **Híbrida:** combinação de elementos preditivos e ágeis conforme as necessidades do projeto.

### Ferramentas populares

- **Quadros visuais e softwares de gestão:** Trello, Asana, Jira, Monday e Microsoft Project.
- **Diagramas e gráficos:** gráfico de Gantt e WBS (*Work Breakdown Structure*, ou Estrutura Analítica do Projeto).

### Estrutura Analítica do Projeto (EAP)

A **Estrutura Analítica do Projeto** (**EAP**; *Work Breakdown Structure*, ou **WBS**) é a decomposição hierárquica do escopo total do projeto em partes menores e mais gerenciáveis, organizadas em torno das entregas e do trabalho necessário para produzi-las. Ela ajuda a definir o que está incluído no projeto, apoiar estimativas de prazo e custo, atribuir responsabilidades e acompanhar o progresso.

A decomposição prossegue até chegar a componentes que possam ser estimados, planejados e controlados, chamados **pacotes de trabalho**. A **regra dos 100%** orienta que a EAP represente todo o escopo aprovado — incluindo o trabalho de gerenciamento — sem omissões nem trabalho fora do escopo. Os elementos de cada nível devem detalhar os componentes do nível superior sem sobreposição.

Exemplo simplificado para um projeto de implantação de um sistema:

```text
1. Sistema implantado
   1.1 Solução configurada
       1.1.1 Requisitos levantados
       1.1.2 Sistema configurado
   1.2 Solução validada
       1.2.1 Testes executados
       1.2.2 Usuários treinados
   1.3 Implantação concluída
       1.3.1 Sistema disponibilizado
       1.3.2 Operação transferida ao suporte
```

O **dicionário da EAP** complementa a estrutura com informações sobre cada componente, como escopo, critérios de aceitação, responsável, premissas e estimativas. A EAP descreve e organiza o escopo; não é, por si só, um cronograma nem precisa representar a sequência temporal das atividades. A ordem e as dependências do trabalho são detalhadas no planejamento do cronograma, por exemplo, com um diagrama de rede ou gráfico de Gantt.

### Método do Caminho Crítico (CPM)

O **Método do Caminho Crítico** (*Critical Path Method*, ou **CPM**) é uma técnica de planejamento e controle de cronogramas. Ele representa as atividades e suas dependências em uma rede para identificar o caminho de maior duração entre o início e o fim do projeto. Esse caminho determina a menor duração possível do cronograma, dadas as durações e dependências estimadas.

Para aplicá-lo:

1. Liste as atividades, suas durações e suas predecessoras (atividades que precisam terminar antes).
2. Represente as dependências em uma rede e calcule as datas mais cedo de início e término de cada atividade, avançando do início ao fim.
3. Faça o cálculo inverso, do fim ao início, para obter as datas mais tarde em que cada atividade pode começar e terminar sem atrasar o projeto.
4. Calcule a **folga total** de cada atividade: a diferença entre as datas mais tarde e mais cedo de início (ou de término). As atividades com folga zero formam um caminho crítico.

Por exemplo, considere as seguintes atividades:

| Atividade | Duração | Predecessoras |
|---|---:|---|
| A | 3 dias | — |
| B | 4 dias | A |
| C | 2 dias | A |
| D | 2 dias | B e C |

Há dois caminhos do início ao fim: **A → B → D**, com 9 dias, e **A → C → D**, com 7 dias. Portanto, **A → B → D** é o caminho crítico e a duração estimada do projeto é de 9 dias. Nesse exemplo, C tem 2 dias de folga; um atraso superior a essa folga pode tornar esse caminho crítico e postergar a conclusão.

As atividades críticas exigem acompanhamento cuidadoso, pois um atraso nelas tende a atrasar a data final, salvo se houver ajustes no cronograma. A duração do caminho crítico pode mudar quando durações ou dependências são atualizadas, e pode haver mais de um caminho crítico. O CPM apoia decisões de priorização e replanejamento, mas suas estimativas não eliminam incertezas nem substituem a análise de recursos e riscos.

### Gerenciamento de Valor Agregado (GVA)

O **Gerenciamento de Valor Agregado** (*Earned Value Management*, ou **EVM**; também chamado de **GVA**) integra escopo, cronograma e custos para avaliar o desempenho do projeto em uma data de controle. A análise compara o trabalho planejado, o trabalho efetivamente concluído e o custo incorrido. Para isso, é necessário ter uma linha de base aprovada e medir o progresso com critérios consistentes.

Os três valores básicos são:

- **Valor Planejado (VP ou PV):** orçamento autorizado para o trabalho que deveria estar concluído até a data de controle.
- **Valor Agregado (VA ou EV):** orçamento previsto para o trabalho que foi efetivamente concluído até essa data. Não é o valor financeiro recebido pelo projeto.
- **Custo Real (CR ou AC):** custo incorrido para realizar o trabalho concluído até a data de controle.

Com esses valores, calculam-se variações e índices:

| Indicador | Fórmula | Interpretação |
|---|---|---|
| **Variação de custo (VC ou CV)** | VA − CR | Positiva: abaixo do orçamento para o trabalho realizado; negativa: acima do orçamento. |
| **Variação de prazo (VPr ou SV)** | VA − VP | Positiva: mais trabalho foi concluído do que o planejado; negativa: menos. É expressa em valor monetário, não em dias. |
| **Índice de desempenho de custos (IDC ou CPI)** | VA ÷ CR | Maior que 1: desempenho favorável de custos; menor que 1: custo acima do valor agregado. |
| **Índice de desempenho de prazo (IDP ou SPI)** | VA ÷ VP | Maior que 1: avanço superior ao planejado; menor que 1: avanço inferior. |

Por exemplo, suponha que, em determinada data, o projeto tenha **VP = R$ 50 mil**, **VA = R$ 40 mil** e **CR = R$ 45 mil**. Então, **VC = −R$ 5 mil** e **VPr = −R$ 10 mil**; além disso, **IDC ≈ 0,89** e **IDP = 0,80**. Isso indica que foi agregado menos valor do que o planejado e que o custo incorrido supera o valor do trabalho concluído.

O GVA também pode apoiar previsões. Se o orçamento no término (**ONT ou BAC**) for R$ 100 mil e se assumir que o desempenho de custos observado continuará, uma estimativa simplificada do custo no término é **ENT = ONT ÷ IDC**; no exemplo, aproximadamente **R$ 112,5 mil**. Essa previsão depende da hipótese adotada: outras fórmulas podem ser mais adequadas quando os desvios são considerados excepcionais ou quando também se leva em conta o desempenho do cronograma.

O GVA fornece indicadores para identificar desvios e apoiar decisões, mas não explica suas causas por si só. Os resultados dependem da qualidade da linha de base, da medição do trabalho concluído e da atualização dos custos; por isso, devem ser analisados junto ao contexto, aos riscos e às mudanças aprovadas.

## 4. Gestão de produto

A **gestão de produtos** é uma prática estratégica que orienta todo o ciclo de vida de um produto — da pesquisa e ideação ao lançamento, às melhorias contínuas e à descontinuação — alinhando objetivos de negócio, tecnologia e experiência do usuário (UX).

### O que faz um gestor de produto (*Product Manager*)

- **Ponte estratégica:** conecta as necessidades dos clientes às metas financeiras da empresa e ao trabalho da equipe de desenvolvimento de tecnologia.
- **Visão e *roadmap*:** define o plano estratégico e o mapa de evolução do produto, priorizando funcionalidades que geram valor.
- **Foco no cliente:** coleta feedback do mercado, estuda personas e orienta o produto para resolver as necessidades reais dos usuários.

### Diferença entre gestão de produto e gestão de projetos

- **Gestão de projetos:** concentra-se em prazos, cronogramas, custos e controle de tarefas para entregar um escopo definido dentro do período previsto.
- **Gestão de produto:** concentra-se no sucesso contínuo, em métricas de valor — como retenção e receita —, na experiência do usuário e na evolução do produto ao longo do tempo.

## 5. Metodologia SAFe

O **Scaled Agile Framework (SAFe)** é um framework usado para ampliar a agilidade ao nível organizacional. Ele conecta a estratégia de negócios à execução diária, ajudando grandes empresas a entregar valor de forma rápida, previsível e consistente.

### Impulso de práticas ágeis em escala

À medida que uma organização cresce, coordenar várias equipes Scrum ou Kanban se torna um desafio. O SAFe organiza essas equipes em redes chamadas **Agile Release Trains (ARTs)**.

- **Agile Release Train (ART):** equipe de equipes, geralmente com 50 a 125 pessoas, que compartilha uma missão de negócio. O ART planeja, executa e entrega valor de forma sincronizada.
- **Release Train Engineer (RTE):** facilita os processos do ART e remove impedimentos em escala, em um papel semelhante ao de um Scrum Master para o trem.
- **Product Management:** define o *backlog* de funcionalidades (*Features*) e a visão do que o ART deve construir.
- **System Architect:** orienta a arquitetura tecnológica para atender às necessidades atuais e futuras do negócio.

### Gestão de portfólio alinhada à estratégia de negócios

O **Lean Portfolio Management (LPM)** ajuda a alinhar o trabalho das equipes aos objetivos estratégicos, para que a agilidade seja aplicada a iniciativas que gerem valor para o negócio. Entre as práticas relacionadas estão:

- **Financiamento de fluxos de valor (*Value Streams*):** em vez de financiar apenas projetos temporários com orçamentos rígidos, os recursos são direcionados a fluxos de valor de longo prazo, permitindo ajustes de prioridade com menos burocracia orçamentária.
- **Epic Kanban e guardrails:** grandes iniciativas (*Epics*) passam por um fluxo visual de análise antes do desenvolvimento. Os *guardrails* definem limites e orientações para o uso dos recursos de cada fluxo de valor.
- **Objetivos e Resultados-Chave (OKRs):** traduzem a estratégia da organização em metas mensuráveis que orientam o trabalho das equipes.

### Realização de entregas incrementais utilizando a metodologia SAFe

A previsibilidade e a entrega contínua são apoiadas por ciclos de trabalho fixos e uma cadência compartilhada.

- **Planejamento do Incremento do Programa (*Program Increment Planning* ou PI Planning):** evento central em que o ART se reúne, presencial ou virtualmente, geralmente por dois dias, para planejar as próximas 8 a 12 semanas. Durante o planejamento, as equipes identificam dependências e riscos.
- **Desenvolver com cadência e liberar sob demanda:** as equipes trabalham em iterações fixas, geralmente de duas semanas, enquanto o negócio pode liberar funcionalidades quando houver necessidade e estiverem prontas.
- **Pipeline de Entrega Contínua (CDP):** conjunto de práticas e automações de DevOps que apoiam a exploração, integração, implantação e liberação contínuas, reduzindo atritos no processo de entrega.

### Benefícios do SAFe

| Área | Abordagem SAFe | Resultado esperado |
|---|---|---|
| **Alinhamento** | Planejamento do Incremento do Programa (PI Planning) | Organização alinhada em torno das prioridades a cada incremento. |
| **Execução** | Agile Release Trains (ARTs) | Sincronização e colaboração entre equipes de tecnologia e negócio. |
| **Estratégia** | Lean Portfolio Management | Recursos direcionados a fluxos de valor, com flexibilidade para ajustar prioridades. |
| **Qualidade** | DevOps e qualidade incorporada | Entregas mais rápidas e redução de falhas em produção. |
