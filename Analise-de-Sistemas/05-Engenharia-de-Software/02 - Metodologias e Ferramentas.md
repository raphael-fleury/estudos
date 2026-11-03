# Metodologias e Ferramentas

## 1. Uso de modelos, metodologias, técnicas e ferramentas de análise e projeto de sistemas (paradigma estruturado e paradigma orientado a objetos)

Análise e projeto transformam necessidades do negócio em uma solução de software. **Analisar** é compreender o problema, os requisitos, os dados e as regras do negócio; **projetar** é definir como a solução será organizada e implementada, incluindo arquitetura, componentes, dados, interfaces e interações. Os modelos ajudam a representar diferentes aspectos do sistema, comunicar decisões e identificar inconsistências antes da construção.

### Modelos, metodologias, técnicas e ferramentas

- **Modelo:** representação simplificada de um aspecto do sistema, como processos, dados, estrutura ou comportamento. Um mesmo sistema pode ter vários modelos complementares.
- **Metodologia ou processo:** organiza atividades, papéis, artefatos e critérios de trabalho. Pode ser preditivo, iterativo, incremental ou ágil; a escolha depende, entre outros fatores, da estabilidade dos requisitos, dos riscos e das necessidades de entrega.
- **Técnica:** procedimento aplicado em uma atividade, como entrevistas, análise de processos, prototipação, modelagem de dados ou revisão de requisitos.
- **Ferramenta:** recurso que apoia as atividades e os artefatos, como editores de diagramas, ferramentas CASE, repositórios de modelos, sistemas de controle de versão e ferramentas de gestão de requisitos.

As ferramentas CASE (*Computer-Aided Software Engineering*) apoiam atividades de engenharia de software. Podem ser **upper CASE**, voltadas às etapas iniciais (análise e projeto), **lower CASE**, voltadas à implementação e aos testes, ou **integradas**, quando cobrem várias etapas. Automatizar a criação de diagramas não garante que o modelo esteja correto: ele ainda precisa ser validado com os stakeholders e mantido consistente com o sistema.

### 1.2. Paradigma estruturado

O paradigma estruturado enfatiza **processos, funções e fluxo de dados**. Decompõe o sistema em funções menores, descrevendo quais entradas são transformadas em saídas e quais dados são armazenados. É especialmente útil para representar processos e sistemas cuja lógica pode ser descrita por transformações bem definidas.

#### Análise estruturada

Na análise, o foco está em **o que o sistema deve fazer**, sem antecipar detalhes de implementação. Entre as técnicas e representações mais comuns estão:

- **Diagrama de fluxo de dados (DFD):** mostra processos, fluxos de dados, depósitos de dados e entidades externas. Os processos transformam dados; os fluxos indicam dados em movimento; os depósitos representam dados armazenados. O DFD descreve o fluxo lógico de dados, não a sequência temporal de execução.
- **Diagrama de contexto:** apresenta o sistema como um único processo e identifica suas fronteiras, as entidades externas e as principais trocas de informação.
- **Decomposição funcional:** divide processos de alto nível em funções e subprocessos, preservando a relação entre os níveis de detalhe.
- **Dicionário de dados:** define o significado, a estrutura e, quando pertinente, o formato dos elementos de dados usados nos modelos.
- **Especificação de processos:** detalha a lógica de processos que não pode ser compreendida apenas pelo DFD, usando linguagem estruturada, tabelas de decisão ou árvores de decisão.
- **Modelo entidade-relacionamento (MER):** representa entidades, atributos e relacionamentos, apoiando a análise dos dados do domínio. O modelo conceitual descreve os dados sem depender de um SGBD específico.

Os níveis de um DFD devem ser consistentes: a entrada e a saída de dados de um processo detalhado precisam corresponder ao fluxo definido no nível superior. Esse princípio é chamado **balanceamento**. Entidades externas normalmente interagem com processos, não diretamente com depósitos de dados.

#### Projeto estruturado

No projeto, a solução é organizada em módulos e interfaces. O **diagrama de estrutura** representa a decomposição hierárquica dos módulos e suas relações de chamada ou comunicação. Um bom projeto busca alta **coesão** (cada módulo tem responsabilidade bem definida) e baixo **acoplamento** (pouca dependência entre módulos), facilitando manutenção e testes.

### 1.3. Paradigma orientado a objetos

O paradigma orientado a objetos organiza o sistema em **objetos**, que combinam estado (dados) e comportamento (operações). A análise identifica conceitos e responsabilidades do domínio; o projeto define como esses conceitos serão realizados por classes, interfaces e componentes de software.

#### Conceitos fundamentais

- **Classe e objeto:** a classe define atributos e operações comuns; o objeto é uma instância com identidade e estado próprios.
- **Abstração:** destaca características relevantes ao problema e omite detalhes desnecessários.
- **Encapsulamento:** reúne estado e comportamento e controla o acesso aos detalhes internos do objeto.
- **Herança:** permite especializar uma classe a partir de outra, reutilizando ou redefinindo características. Deve ser usada quando existe uma relação de especialização coerente, não apenas para reutilizar código.
- **Polimorfismo:** permite que objetos de tipos diferentes respondam à mesma operação de acordo com sua implementação.
- **Associação, agregação e composição:** representam relações entre objetos. Agregação indica uma relação todo-parte mais fraca; composição indica vínculo mais forte, no qual as partes pertencem ao ciclo de vida do todo.

#### Análise, projeto e UML

A **UML (Unified Modeling Language)** é uma linguagem de modelagem, não uma metodologia ou um processo de desenvolvimento. Seus diagramas podem representar estrutura ou comportamento, por exemplo:

- **Casos de uso:** representam atores e objetivos/serviços oferecidos pelo sistema; ajudam a delimitar funcionalidades, mas não descrevem, sozinhos, toda a lógica interna.
- **Classes:** mostram classes, atributos, operações e relações, como associação, generalização e dependência.
- **Sequência:** mostra a ordem temporal das mensagens trocadas entre participantes em um cenário.
- **Atividades:** representa fluxos de trabalho, decisões, paralelismo e responsabilidades.
- **Estados:** mostra estados possíveis de um objeto e as transições provocadas por eventos.
- **Componentes e implantação:** representam, respectivamente, a organização de componentes de software e sua distribuição em nós de execução.

Modelos de caso de uso e de domínio são comuns na análise; diagramas de classes de projeto, sequência e componentes ajudam a detalhar a solução. A UML pode ser usada em processos diferentes, como o Processo Unificado (UP/RUP), e também em abordagens ágeis, com documentação proporcional à necessidade.

### 1.4. Comparação dos paradigmas

| Aspecto | Estruturado | Orientado a objetos |
|---|---|---|
| Unidade de decomposição | Processos e funções | Objetos e classes |
| Ênfase | Transformação e fluxo de dados | Estado, comportamento e colaboração |
| Modelos frequentes | DFD, dicionário de dados, MER, diagrama de estrutura | Casos de uso, classes, sequência, atividades e estados (UML) |
| Organização da solução | Módulos funcionais | Objetos e componentes com responsabilidades |
| Mudanças | Podem exigir alterações em processos e estruturas de dados relacionadas | Podem ser localizadas quando responsabilidades e interfaces estão bem definidas |

Os paradigmas não são sinônimos de linguagens de programação nem determinam, isoladamente, uma metodologia. Na prática, podem coexistir: por exemplo, a análise de processos pode usar DFD e a solução ser projetada com classes e componentes. O essencial é que os modelos escolhidos sejam adequados ao problema e coerentes entre si.

### 1.5. Boas práticas de modelagem

- Escolher o nível de detalhe adequado ao público e à decisão que o modelo deve apoiar.
- Definir termos e regras de negócio de forma consistente, evitando ambiguidades.
- Validar os modelos com usuários, especialistas do domínio e equipe técnica.
- Manter rastreabilidade entre requisitos, modelos, componentes e testes.
- Revisar consistência e completude; diagramas devem complementar, e não substituir, requisitos e explicações necessárias.
- Evitar documentação excessiva ou modelos desatualizados: registrar o que ajuda a comunicar, analisar, construir ou manter a solução.

## 2. Verificação, validação e teste

Na Engenharia de Software, **Verificação, Validação e Teste** são práticas fundamentais para avaliar a qualidade e a confiabilidade do sistema e verificar se ele atende aos requisitos e objetivos propostos. Verificação e validação (V&V) são atividades relacionadas, mas respondem a perguntas diferentes.

### 2.1. Verificação: construir o produto do jeito certo

A verificação avalia se o produto está sendo desenvolvido em conformidade com os requisitos, especificações e critérios definidos para cada etapa.

- **Pergunta-chave:** “Estamos construindo o produto corretamente?”
- **Foco:** conformidade com requisitos, projeto e normas aplicáveis.
- **Natureza:** pode ser estática, sem executar o código, ou dinâmica, com execução.
- **Exemplos:** revisão de requisitos e arquitetura, inspeção de código, análise estática e testes de unidade ou integração projetados para verificar requisitos especificados.

### 2.2. Validação: construir o produto certo

A validação avalia se o sistema atende às necessidades reais dos usuários e ao propósito de uso no contexto previsto.

- **Pergunta-chave:** “Estamos construindo o produto certo?”
- **Foco:** adequação ao uso, às expectativas dos usuários e aos objetivos de negócio.
- **Natureza:** frequentemente dinâmica e realizada com participação de usuários ou representantes do negócio; também pode incluir avaliações e revisões sem execução do software.
- **Exemplos:** testes de aceitação, testes de usabilidade e avaliação do sistema em um ambiente representativo de uso.

### 2.3. Teste de software

Teste de software é um conjunto de atividades que pode envolver executar o programa com entradas selecionadas, comparar os resultados observados com os esperados e identificar falhas ou avaliar atributos de qualidade. Testes também incluem atividades estáticas, como revisão e análise de artefatos, embora o teste dinâmico envolva a execução do software.

Os testes podem apoiar tanto a verificação quanto a validação: por exemplo, um teste de integração pode verificar a conformidade com uma especificação, enquanto um teste de aceitação pode validar se a solução atende aos critérios de negócio. **O nível do teste, por si só, não define se ele é verificação ou validação; isso depende do objetivo e dos critérios usados.**

#### Níveis comuns de teste

1. **Teste de unidade:** verifica componentes, funções ou unidades de código de forma isolada.
2. **Teste de integração:** verifica a interação e a troca de dados entre módulos ou componentes.
3. **Teste de sistema:** avalia o sistema integrado em relação aos requisitos especificados.
4. **Teste de aceitação:** avalia se o sistema atende aos critérios de aceitação e às necessidades do negócio e dos usuários.

### 2.4. Resumo comparativo

| Conceito | Foco principal | Executa o código? | Pergunta central |
|---|---|---|---|
| **Verificação** | Conformidade com especificações, requisitos e normas | Nem sempre; pode ser estática ou dinâmica | “Estamos construindo o produto corretamente?” |
| **Validação** | Necessidades dos usuários e adequação ao propósito de uso | Frequentemente sim, mas também pode envolver avaliações sem execução | “Estamos construindo o produto certo?” |
| **Teste** | Avaliação do comportamento e da qualidade; identificação de falhas | Testes dinâmicos sim; atividades estáticas não | “O que acontece quando avaliamos o produto?” |

## 3. Ambientes de desenvolvimento de software

Um **ambiente de desenvolvimento de software** reúne hardware, sistemas operacionais, ferramentas, bibliotecas, serviços, configurações e dados usados para criar, executar, testar e manter aplicações. Um ambiente bem definido facilita a colaboração, reduz diferenças entre máquinas e ajuda a entregar versões reproduzíveis e confiáveis.

### 3.1. Componentes do ambiente

- **Hardware e sistema operacional:** recursos de processamento, memória, armazenamento e sistema sobre o qual as ferramentas e aplicações são executadas.
- **Linguagens e runtimes:** linguagens de programação, compiladores, interpretadores e ambientes de execução necessários para construir ou executar o software.
- **IDE e editores:** oferecem recursos como edição, navegação no código, refatoração, integração com depurador e execução de tarefas. Também é possível desenvolver com ferramentas de linha de comando.
- **Depuradores e ferramentas de diagnóstico:** ajudam a observar a execução, inspecionar variáveis, acompanhar chamadas e investigar falhas.
- **Ferramentas de build e automação:** compilam, empacotam e executam tarefas repetíveis, como análise estática e testes.
- **Bibliotecas, frameworks e gerenciadores de pacotes:** fornecem componentes reutilizáveis e controlam dependências. Versões e fontes das dependências devem ser registradas para permitir instalações consistentes.
- **Controle de versão:** mantém o histórico das alterações e permite colaboração, revisão de código e recuperação de versões. O Git é um exemplo de sistema distribuído de controle de versão.
- **Serviços de apoio:** bancos de dados, filas, serviços de identidade, APIs e outros componentes de que a aplicação depende. Em desenvolvimento, podem ser locais, compartilhados ou simulados.

### 3.2. Ambientes ao longo do ciclo de entrega

É comum separar ambientes para limitar riscos e controlar a progressão de uma alteração. Os nomes e a quantidade variam entre organizações, e nem todo projeto precisa de ambientes separados para cada etapa.

1. **Desenvolvimento (development):** usado pela equipe para implementar funcionalidades e realizar verificações iniciais. Pode conter configurações e dados locais ou de teste.
2. **Integração ou teste (integration/test):** recebe alterações para avaliar a integração entre componentes e executar testes automatizados ou manuais em condições controladas.
3. **Homologação ou pré-produção (staging):** procura reproduzir aspectos relevantes da produção e permite validações finais, como testes de aceitação. Não deve ser confundida com o ambiente produtivo.
4. **Produção (production):** ambiente em que o sistema atende usuários reais. Mudanças são implantadas de forma controlada, com monitoramento e procedimentos de recuperação.

Separar ambientes ajuda a proteger dados e serviços produtivos, mas exige manter as configurações compatíveis. O acesso deve ser concedido conforme a necessidade e ambientes não produtivos devem usar dados fictícios ou devidamente protegidos, em vez de expor dados pessoais ou confidenciais sem autorização.

### 3.3. Integração, entrega e implantação contínuas

A **integração contínua (CI)** automatiza a integração frequente de alterações e executa verificações, como build, testes e análise de código, para detectar problemas cedo. A **entrega contínua** mantém o software em condição de ser liberado, normalmente com a decisão de publicação ainda sujeita a aprovação. Na **implantação contínua**, alterações que passam pelas verificações podem ser publicadas automaticamente em produção, conforme as regras da organização.

Pipelines de CI/CD (*Continuous Integration/Continuous Delivery or Deployment*) descrevem essas etapas automatizadas. Um pipeline típico pode:

1. obter o código versionado e instalar dependências;
2. compilar ou empacotar a aplicação;
3. executar verificações de qualidade e testes;
4. gerar e armazenar um artefato versionado;
5. implantar o artefato em um ambiente e executar verificações posteriores.

Automatizar não elimina a necessidade de testes, revisão, aprovação ou monitoramento. A estratégia de implantação deve considerar o impacto de falhas e permitir identificar e reverter ou corrigir uma versão problemática.

### 3.4. Configuração, contêineres e reprodutibilidade

- **Configuração por ambiente:** parâmetros que variam entre ambientes, como endereços de serviços e níveis de log, devem ser separados do código e gerenciados de forma controlada.
- **Segredos:** senhas, chaves e tokens devem ser armazenados em mecanismos apropriados de gestão de segredos, não no código-fonte, em imagens públicas ou em arquivos versionados sem proteção.
- **Contêineres:** empacotam a aplicação e suas dependências de execução em uma unidade isolada, facilitando consistência entre ambientes. Não substituem automaticamente máquinas virtuais, controles de segurança ou o gerenciamento de dados persistentes.
- **Infraestrutura como código (IaC):** permite declarar e versionar a configuração de infraestrutura para automatizar sua criação e reduzir divergências entre ambientes.
- **Reprodutibilidade:** versões fixadas de ferramentas e dependências, scripts de configuração e documentação de execução ajudam diferentes pessoas e sistemas a obter resultados compatíveis.

### 3.5. Boas práticas

- Padronizar e documentar os passos para configurar, executar e testar o projeto.
- Versionar código, scripts de automação e arquivos de configuração não sensíveis; revisar alterações antes de integrá-las.
- Manter dependências atualizadas e controladas, avaliando compatibilidade e riscos antes de atualizações.
- Executar testes e verificações automatizadas de forma consistente, de preferência também em integração contínua.
- Restringir acessos por ambiente e não usar dados produtivos sem autorização e medidas de proteção adequadas.
- Monitorar aplicações implantadas e manter procedimentos de backup, recuperação e reversão compatíveis com a criticidade do sistema.
