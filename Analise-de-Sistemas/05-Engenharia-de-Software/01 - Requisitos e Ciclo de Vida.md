# Requisitos e Ciclo de Vida

## 1. Levantamento, análise e gerenciamento de requisitos

O levantamento, análise e gerenciamento de requisitos formam a base da Engenharia de Requisitos, garantindo que um software ou projeto seja construído exatamente para resolver o problema certo, evitando custos e retrabalhos.

### 1.1. Levantamento (elicitação)

É o processo de descobrir e coletar as necessidades, os desejos e as restrições junto aos stakeholders (partes interessadas, clientes, usuários finais e equipe de gestão).

#### Principais técnicas
- **Entrevistas:** conversas estruturadas, semiestruturadas ou abertas com os usuários.
- **Brainstorming:** reuniões criativas em grupo para gerar ideias e funcionalidades.
- **Prototipagem:** construção de modelos visuais rápidos para validar a ideia com o cliente.
- **Observação (shadowing):** acompanhamento do usuário em sua rotina de trabalho real.
- **Workshops e grupos focais:** sessões colaborativas para alinhar as expectativas de múltiplos setores.

#### Tipos de requisitos identificados
- **Funcionais:** descrevem o que o sistema faz. Exemplo: “o usuário deve conseguir redefinir a senha por e-mail”.
- **Não funcionais:** definem atributos de qualidade e restrições. Exemplos: “o sistema deve carregar em até 2 segundos”, segurança e conformidade.
- **De domínio:** representam regras específicas da área de negócio. Exemplos: leis contábeis ou normas médicas.

### 1.2. Análise, negociação e especificação

Nesta fase, as informações coletadas são refinadas, organizadas e traduzidas para uma linguagem técnica compreensível para os desenvolvedores, eliminando ambiguidades e conflitos.

- **Modelagem:** uso de diagramas (como casos de uso, fluxogramas e BPMN) ou histórias de usuário (*user stories*).
- **Resolução de conflitos:** negociação de prioridades e viabilidade técnica quando dois stakeholders têm pedidos contraditórios.
- **Verificação e validação:** conferência de que o requisito está bem escrito (verificação) e de que corresponde ao que o cliente precisa (validação), muitas vezes por meio de revisão por pares (*peer review*).
- **Documentação (SRS):** criação da Especificação de Requisitos de Software, documento que formaliza o acordo entre cliente e equipe.

### 1.3. Gerenciamento

É a disciplina contínua de acompanhar, controlar e rastrear os requisitos ao longo de todo o ciclo de vida do projeto.

- **Rastreabilidade:** identificação da origem de cada requisito e de quais partes do código ou testes o atendem, mantendo uma ligação bidirecional.
- **Controle de mudanças:** definição de um fluxo formal para solicitações de alteração, com análise de impacto em prazo, custo e recursos antes da aprovação.
- **Priorização:** definição do que fará parte do MVP (Produto Mínimo Viável) e do que ficará para versões futuras.
- **Ferramentas de apoio:** uso de plataformas como Jira, Confluence, Trello ou IBM Engineering Requirements Management para centralizar a documentação.

## 2. Ciclo de vida de sistemas e seus paradigmas

O Ciclo de Vida de Desenvolvimento de Sistemas (SDLC) é a estrutura que orienta a criação, a operação e a desativação de um sistema. Ele transforma um processo que poderia ser caótico em etapas organizadas e previsíveis.

### 2.1. Fases principais do ciclo de vida

O modelo clássico e mais amplo de SDLC divide-se em sete etapas fundamentais:

1. **Planejamento:** definição dos objetivos, do escopo, dos custos, dos prazos e da viabilidade do projeto.
2. **Análise de requisitos:** levantamento detalhado do que o sistema precisa fazer e dos problemas que deve resolver.
3. **Projeto (design):** definição da arquitetura técnica, do banco de dados, dos fluxos e da interface do usuário.
4. **Desenvolvimento (codificação):** escrita do código e construção dos módulos do sistema.
5. **Testes:** validação da qualidade, verificação de falhas e execução de testes de integração, de sistema e de aceitação.
6. **Implantação (deploy):** lançamento e disponibilização do sistema para os usuários finais.
7. **Manutenção:** correção de falhas, atualizações e adaptações a novas tecnologias.

### 2.2. Principais paradigmas e modelos

Os paradigmas e modelos de ciclo de vida definem como essas fases são executadas ao longo do tempo:

- **Modelo em Cascata (Waterfall):** sequencial e rígido. Cada etapa precisa ser concluída antes do início da seguinte. É adequado para requisitos fixos e bem conhecidos, mas pouco flexível a mudanças.
- **Modelo em V:** variação da cascata em que cada fase de desenvolvimento possui uma fase de testes correspondente. Por exemplo, o projeto de alto nível se relaciona aos testes de aceitação.
- **Modelo iterativo e incremental:** o sistema é construído em partes ou versões, que recebem novas funcionalidades a cada ciclo.
- **Modelo em Espiral:** fortemente focado na gestão de riscos. A cada iteração, os riscos são analisados e novos protótipos podem ser gerados.
- **Prototipagem:** construção rápida de modelos visuais ou funcionais para validar os requisitos com o cliente antes do desenvolvimento final.
- **Paradigma ágil (Scrum, Kanban):** baseado em entregas rápidas, flexibilidade, colaboração próxima com o cliente e adaptação contínua a mudanças nos requisitos.
- **DevOps / DevSecOps:** integração entre desenvolvimento (Dev) e operações (Ops), com automação contínua de testes, entrega e segurança (Sec).
- **IA aumentada no SDLC (AI-augmented SDLC):** paradigma emergente em que ferramentas e agentes de inteligência artificial auxiliam ou executam partes do ciclo de vida, da geração de código aos testes e à implantação.
