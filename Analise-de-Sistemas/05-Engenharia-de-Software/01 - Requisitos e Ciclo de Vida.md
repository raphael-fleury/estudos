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
