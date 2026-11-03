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
## 3. Ambientes de desenvolvimento de software
