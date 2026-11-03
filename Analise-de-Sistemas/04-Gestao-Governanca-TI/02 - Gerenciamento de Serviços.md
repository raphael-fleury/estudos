# Gerenciamento de Serviços

## 1. Conceitos, disciplinas, técnicas e ferramentas de gerenciamento de serviços de TI

Gerenciamento de serviços de TI (GSTI, ou ITSM — *IT Service Management*) é o conjunto de capacidades organizacionais usado para planejar, entregar, operar e melhorar serviços de TI. Seu objetivo é apoiar os resultados dos clientes e da organização, equilibrando valor, custo, risco, qualidade e experiência do usuário.

### Conceitos fundamentais

- **Serviço:** meio de permitir que clientes alcancem resultados desejados sem que precisem gerenciar diretamente determinados custos e riscos. O serviço não elimina todos os custos ou riscos: parte deles continua com o consumidor.
- **Produto:** conjunto de recursos de uma organização que pode ser disponibilizado para criar valor. Um serviço pode combinar produtos, pessoas, processos, informação e tecnologia.
- **Oferta de serviço:** descrição formal de um ou mais serviços para um grupo de consumidores. Pode incluir acesso a recursos, ações executadas pelo provedor e fornecimento de bens.
- **Valor:** benefício, utilidade ou importância percebida por quem recebe ou fornece o serviço. O valor é cocriado por provedores, consumidores e demais partes interessadas.
- **Resultado (*outcome*):** consequência ou resultado possibilitado pelo serviço para uma parte interessada. Diferencia-se de uma **saída (*output*)**, que é um produto ou entrega direta de uma atividade.
- **Utilidade e garantia:** utilidade é o que o serviço faz e se atende à necessidade; garantia é a confiança de que ele estará disponível e adequado ao uso, considerando aspectos como capacidade, disponibilidade, continuidade e segurança.
- **Cliente, usuário e patrocinador:** cliente define requisitos e responde pelos resultados do consumo; usuário utiliza o serviço; patrocinador autoriza o orçamento. Uma pessoa pode exercer mais de um desses papéis.
- **Provedor e consumidor:** o provedor entrega e administra o serviço; o consumidor recebe ou utiliza o serviço, podendo atuar como cliente, usuário ou patrocinador.

O gerenciamento de serviços considera o ciclo de vida completo: demanda e desenho, transição para produção, entrega e suporte, medição e melhoria contínua.

### ITIL 4

ITIL 4 é um conjunto de orientações para gerenciamento de serviços, organizado em torno do **Sistema de Valor de Serviço (SVS)**. O SVS descreve como componentes e atividades da organização trabalham juntos para facilitar a criação de valor.

Os componentes do SVS são:

- **Princípios orientadores:** recomendações aplicáveis a diferentes situações, como focar no valor, começar de onde se está, progredir iterativamente com feedback, colaborar e promover visibilidade, pensar e trabalhar holisticamente, manter simplicidade e otimizar e automatizar.
- **Governança:** direciona e monitora a organização, avaliando necessidades das partes interessadas, orientando decisões e acompanhando resultados.
- **Cadeia de valor de serviço:** modelo operacional com seis atividades interligadas:
	- **Planejar:** criar entendimento compartilhado de visão, situação atual e direção.
	- **Melhorar:** aperfeiçoar produtos, serviços e práticas continuamente.
	- **Engajar:** compreender necessidades e manter relacionamento com partes interessadas.
	- **Desenhar e transicionar:** assegurar que produtos e serviços atendam aos requisitos de qualidade, custo e prazo.
	- **Obter/construir:** disponibilizar componentes necessários, adquiridos ou desenvolvidos.
	- **Entregar e suportar:** operar serviços e prestar suporte conforme os níveis acordados.
- **Práticas:** recursos organizacionais — pessoas, processos, informação, tecnologia e parceiros — usados para executar trabalho e atingir objetivos.
- **Melhoria contínua:** atividade permanente que alinha serviços às necessidades em mudança e aumenta sua efetividade.

As atividades da cadeia podem ser combinadas em diferentes fluxos de valor, conforme a demanda. Portanto, a cadeia não deve ser interpretada como uma sequência rígida e única.

### Dimensões do gerenciamento de serviços

O ITIL 4 recomenda considerar quatro dimensões para evitar decisões isoladas:

1. **Organizações e pessoas:** estrutura, cultura, papéis, competências e capacidade de colaboração.
2. **Informação e tecnologia:** dados, conhecimento, aplicações, infraestrutura, automação e segurança.
3. **Parceiros e fornecedores:** relações externas e componentes obtidos de terceiros.
4. **Fluxos de valor e processos:** atividades, controles e formas de trabalho necessárias para entregar valor.

Fatores externos, como legislação, economia, sociedade, tecnologia, ambiente e regras aplicáveis, também podem influenciar as decisões.

### Práticas e disciplinas importantes

O ITIL 4 define 34 práticas. Entre as mais recorrentes na operação de serviços estão:

- **Central de serviço (*service desk*):** ponto de contato entre o provedor e os usuários; registra demandas e facilita a comunicação e o suporte.
- **Gerenciamento de incidentes:** restaura a operação normal do serviço o mais rápido possível e reduz o impacto de interrupções. Incidente é uma interrupção não planejada ou redução da qualidade do serviço.
- **Gerenciamento de requisições de serviço:** trata solicitações predefinidas e iniciadas pelo usuário, como acesso, informação ou instalação autorizada. Requisição não é necessariamente incidente.
- **Gerenciamento de problemas:** identifica causas reais ou potenciais de incidentes e administra soluções de contorno e erros conhecidos. Um problema pode existir sem incidente já observado.
- **Habilitação de mudanças (*change enablement*):** avalia riscos, autoriza mudanças e administra seu calendário para maximizar mudanças bem-sucedidas. Mudança padrão, normal e emergencial podem exigir controles diferentes.
- **Gerenciamento de configuração de serviço:** mantém informações sobre itens de configuração e seus relacionamentos, apoiando a compreensão dos serviços e dos impactos de mudanças.
- **Gerenciamento de ativos de TI:** acompanha ativos ao longo do ciclo de vida, incluindo aquisição, uso, manutenção e descarte, considerando valor, custo, risco e obrigações.
- **Gerenciamento de nível de serviço:** define, acorda e acompanha metas de qualidade com os clientes, como disponibilidade e tempos de resposta.
- **Gerenciamento de disponibilidade, capacidade e desempenho:** assegura que os serviços atendam às necessidades de operação, volume e desempenho acordadas.
- **Gerenciamento de continuidade de serviço:** prepara a organização para manter ou recuperar serviços após interrupções graves.
- **Gerenciamento de segurança da informação:** protege confidencialidade, integridade e disponibilidade das informações e dos serviços.
- **Gerenciamento de conhecimento:** torna informações confiáveis acessíveis a quem precisa delas, reduzindo retrabalho e acelerando decisões e suporte.
- **Monitoramento e gerenciamento de eventos:** observa serviços e componentes, identifica mudanças de estado relevantes e aciona respostas apropriadas.
- **Gerenciamento de fornecedores:** administra contratos, desempenho e riscos associados a fornecedores e serviços externos.
- **Gerenciamento de implantação e de liberação:** implantação disponibiliza componentes em ambientes; liberação torna funcionalidades ou serviços disponíveis para uso. São atividades relacionadas, mas distintas.

### Acordos e indicadores

- **SLA (*Service Level Agreement*):** acordo de nível de serviço entre provedor e cliente, com metas e responsabilidades relacionadas ao serviço.
- **OLA (*Operational Level Agreement*):** acordo interno entre equipes ou unidades do provedor que sustenta o cumprimento do SLA.
- **Contrato de apoio (*underpinning contract*):** acordo com fornecedor externo que contribui para a entrega do serviço.
- **Indicadores:** devem refletir resultados e qualidade percebida, além do volume de atividades. Exemplos incluem disponibilidade, tempo de restauração, cumprimento de metas acordadas, recorrência de incidentes e satisfação dos usuários.

Um SLA precisa ter escopo, método de medição, período de apuração, responsabilidades e metas claros. Atingir um indicador isolado não garante valor se a experiência ou o resultado do usuário for inadequado.

### Técnicas de trabalho

- **Priorização de incidentes:** considerar impacto no negócio e urgência para estabelecer prioridade e ordem de atendimento; prioridade não deve depender apenas de quem abriu o chamado.
- **Análise de causa raiz:** usar técnicas como os cinco porquês e diagrama de causa e efeito para investigar fatores contribuintes, em vez de tratar somente os sintomas.
- **Gestão do conhecimento:** registrar soluções verificadas, procedimentos e informações conhecidas em artigos pesquisáveis, com responsáveis por revisão e atualização.
- **Gestão de mudanças baseada em risco:** avaliar impacto, probabilidade, dependências, plano de implantação, comunicação e possibilidade de retorno antes de autorizar mudanças.
- **Melhoria contínua:** identificar uma oportunidade, entender a situação atual, definir um estado desejado, executar ações, medir resultados e incorporar o aprendizado.
- **Automação:** automatizar tarefas repetitivas e controláveis após compreender e simplificar o processo. Automação de um processo inadequado pode apenas acelerar erros.

### Ferramentas de apoio

Ferramentas apoiam as práticas, mas não substituem papéis claros, processos adequados, conhecimento e governança. Categorias comuns incluem:

- **Plataforma ITSM:** registro e acompanhamento de incidentes, requisições, mudanças, problemas, aprovações, catálogo e SLAs.
- **Catálogo de serviços e portal de autoatendimento:** apresentam serviços e requisições disponíveis e permitem que usuários acompanhem suas solicitações.
- **CMDB e descoberta de ativos:** armazenam itens de configuração e relacionamentos; ferramentas de descoberta ajudam a identificar componentes e alterações no ambiente.
- **Monitoramento e observabilidade:** coletam métricas, logs, rastros e eventos para identificar falhas, degradação e tendências.
- **Gestão de conhecimento e colaboração:** organizam procedimentos, soluções conhecidas e comunicação entre equipes.
- **Automação e orquestração:** executam tarefas e fluxos de trabalho, como provisionamento padronizado e aplicação de rotinas operacionais.
- **Relatórios e painéis:** consolidam indicadores para acompanhar qualidade, demanda, desempenho e oportunidades de melhoria.

### Normas e abordagens relacionadas

- **ISO/IEC 20000-1:** norma internacional que especifica requisitos para estabelecer, implementar, manter e melhorar um sistema de gerenciamento de serviços.
- **ITIL:** orientação e boas práticas que podem apoiar o desenho e a operação do gerenciamento de serviços; não é, por si só, uma norma de requisitos equivalente à ISO/IEC 20000-1.
- **DevOps e SRE:** abordagens que podem complementar o gerenciamento de serviços ao aproximar desenvolvimento e operação, automatizar entregas e dar atenção explícita à confiabilidade. Não eliminam a necessidade de gestão de serviços, suporte, riscos e responsabilidades.
