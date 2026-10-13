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
