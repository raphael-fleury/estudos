# Conceitos Básicos

## 1. Segurança física e lógica

A **segurança física** e a **segurança lógica** são pilares complementares da proteção dos ativos de uma organização. A primeira protege instalações, equipamentos e pessoas contra ameaças físicas; a segunda protege dados, aplicações e sistemas contra acessos e ações não autorizados. Como os ambientes físicos e digitais estão conectados, controles eficazes geralmente combinam as duas.

### Segurança física

Protege os ativos tangíveis e a infraestrutura contra acesso não autorizado, danos, perda ou interrupção. Entre os ativos protegidos estão prédios, salas técnicas, servidores, estações de trabalho, mídias e equipamentos de rede.

Exemplos de ameaças físicas incluem furto, vandalismo, incêndio, inundação, falta de energia e entrada de pessoas não autorizadas. Controles comuns incluem:

- portarias, identificação, catracas e registro de visitantes;
- fechaduras, cartões de acesso e restrição de áreas sensíveis;
- câmeras, alarmes, vigilância e sensores ambientais;
- proteção contra incêndio, climatização e fornecimento de energia de contingência;
- guarda, transporte e descarte seguro de equipamentos e mídias.

### Segurança lógica

Protege os ativos digitais — como informações, contas, aplicações, sistemas e redes — contra acesso, uso, alteração ou destruição não autorizados. A proteção busca preservar a **confidencialidade**, a **integridade** e a **disponibilidade** das informações.

Controles comuns incluem:

- autenticação, autorização e princípio do menor privilégio;
- senhas fortes, autenticação multifator e gestão de identidades;
- criptografia de dados armazenados e transmitidos;
- atualizações, configurações seguras e proteção contra códigos maliciosos;
- registro e monitoração de atividades, cópias de segurança e recuperação.

### Integração entre os controles

Um controle isolado não é suficiente. Por exemplo, uma sala de servidores pode ter acesso físico restrito, mas ainda precisa de contas individuais, permissões adequadas e monitoramento dos sistemas. Da mesma forma, controles digitais não impedem que um equipamento desprotegido seja furtado ou danificado. A combinação de medidas físicas e lógicas reduz riscos e contribui para a continuidade dos serviços.

## 2. Operação de segurança (Firewall, Proxy, IPS/IDS, DLP, CASB, SIEM, Antivírus, EDR, WAF, Gestão de vulnerabilidades, Monitoração, Backup)

### Firewall

Um **firewall** é um componente de segurança, implementado em hardware, software ou ambos, que controla o tráfego de rede de acordo com regras definidas. Ele pode proteger uma rede, um segmento ou um dispositivo, permitindo ou bloqueando comunicações entre diferentes zonas. Não se deve presumir que toda rede interna é confiável: as regras devem considerar a origem, o destino e o contexto de cada conexão.

#### Funções

- **Filtrar tráfego:** permitir ou bloquear conexões de entrada e saída conforme a política de segurança.
- **Avaliar conexões:** considerar informações como endereços IP de origem e destino, portas, protocolos e, conforme o tipo de firewall, o estado da conexão ou a aplicação.
- **Aplicar políticas de acesso:** reduzir comunicações desnecessárias e limitar a exposição de sistemas e serviços.
- **Registrar eventos:** produzir registros que apoiem a monitoração, a auditoria e a investigação de incidentes.

O firewall atua como uma barreira de controle, mas não garante, sozinho, a proteção contra toda atividade maliciosa. Sua eficácia depende de regras adequadas, manutenção e integração com outros controles de segurança.

#### Tipos e métodos

**Quanto à forma de implantação:**

- **Firewall de rede (appliance):** equipamento dedicado ou função integrada a dispositivos de rede, usado para controlar o tráfego entre redes ou segmentos.
- **Firewall de host:** software executado em um computador ou servidor, que controla as conexões daquele dispositivo.

**Quanto à análise do tráfego:**

- **Stateless (sem estado):** avalia cada pacote individualmente, usando critérios definidos nas regras, sem acompanhar o estado da conexão.
- **Stateful (com estado):** mantém informações sobre conexões ativas e usa esse contexto para avaliar os pacotes, distinguindo melhor o tráfego associado a conexões estabelecidas.
- **NGFW (Next-Generation Firewall):** firewall de próxima geração que pode combinar filtragem tradicional com recursos como identificação de aplicações e prevenção de intrusões (IPS). Os recursos disponíveis variam conforme o produto e a configuração.

### Proxy

Um **proxy** é um sistema intermediário que recebe solicitações de um cliente e as encaminha a um servidor de destino. A resposta retorna pelo proxy antes de chegar ao cliente. Em uma navegação web encaminhada por um proxy, o servidor de destino normalmente vê o endereço IP do proxy como origem da conexão; no entanto, a configuração e os cabeçalhos utilizados podem revelar informações sobre o cliente. Portanto, um proxy não garante anonimato nem substitui outros controles de segurança.

#### Funções comuns

- **Controle de acesso e filtragem:** aplicar políticas de navegação, como permitir ou bloquear categorias de sites e serviços.
- **Registro e auditoria:** registrar solicitações para monitoração e investigação, respeitando as políticas de privacidade e retenção aplicáveis.
- **Cache:** armazenar temporariamente conteúdos que podem ser reutilizados, reduzindo solicitações repetidas e o consumo de banda quando o conteúdo permite cache.
- **Intermediação e proteção:** evitar conexões diretas entre clientes e determinados servidores e aplicar verificações ou políticas adicionais.
- **Desempenho e disponibilidade:** um proxy reverso pode distribuir solicitações entre servidores e, dependendo da arquitetura, contribuir para cache e terminação TLS.

#### Tipos de proxy

- **Forward proxy (proxy de encaminhamento):** atua em nome dos clientes de uma rede, intermediando o acesso a servidores externos. É comum em organizações para aplicar políticas de navegação e controle.
- **Reverse proxy (proxy reverso):** recebe solicitações destinadas a servidores internos e as encaminha aos serviços apropriados. Pode ocultar detalhes da infraestrutura de origem, distribuir tráfego e integrar recursos de segurança.
- **Transparente:** é configurado para que o cliente não precise definir explicitamente o proxy; ainda pode ser percebido por aplicações ou protocolos, e não deve ser entendido como mecanismo de anonimato.
- **Anônimo e de alta anonimidade (elite):** classificações relacionadas às informações que o proxy revela ao destino sobre o cliente e sobre o uso de um proxy. O comportamento depende da configuração e não constitui garantia de privacidade.

Proxy e firewall podem atuar em conjunto, mas têm funções distintas: o firewall controla o tráfego conforme regras de rede, enquanto o proxy intermedeia solicitações em protocolos ou aplicações compatíveis. O uso de um não elimina a necessidade do outro.

### IDS e IPS

O **IDS (Sistema de Detecção de Intrusão)** e o **IPS (Sistema de Prevenção de Intrusão)** monitoram o tráfego da rede em busca de ameaças conhecidas ou atividades anômalas, mas diferem na forma de atuação.

#### IDS (Intrusion Detection System)

- **Como funciona:** atua de forma passiva, monitorando o tráfego da rede — geralmente por meio de uma porta espelhada ou de um *tap* — e comparando as atividades com assinaturas de ameaças conhecidas ou padrões de anomalia.
- **Ação:** detecta eventos suspeitos e gera alertas para a equipe de segurança, sem alterar nem bloquear os pacotes de rede.
- **Vantagem:** como o tráfego não passa diretamente pelo IDS, ele não adiciona latência ao fluxo da rede.

#### IPS (Intrusion Prevention System)

- **Como funciona:** atua de forma ativa e fica posicionado *inline*, no caminho direto do tráfego. Todo o tráfego passa por ele para ser inspecionado em tempo real.
- **Ação:** além de detectar ameaças, pode bloquear ou descartar pacotes e encerrar conexões para impedir um ataque.
- **Vantagem:** pode evitar invasões de forma proativa. Como analisa o tráfego em linha, pode introduzir uma pequena latência na rede.

### DLP (Data Loss Prevention)

O **DLP (Prevenção contra Perda de Dados)** é uma estratégia e um conjunto de soluções de segurança voltados a identificar, monitorar e proteger informações confidenciais contra vazamento, exposição ou uso indevido. As ferramentas podem classificar dados por padrões, conteúdo ou contexto e aplicar políticas conforme o tipo de informação e a ação realizada.

#### Como funciona

1. **Identificação e classificação:** localiza e classifica dados sensíveis, como documentos estratégicos, propriedade intelectual, números de identificação pessoal e dados de cartões de crédito.
2. **Monitoramento:** acompanha o uso e a movimentação das informações, como envio por e-mail, uploads, downloads, cópias para mídias removíveis e compartilhamentos.
3. **Proteção e resposta:** conforme as regras configuradas, pode alertar o usuário ou a equipe de segurança, restringir o compartilhamento, criptografar o conteúdo ou bloquear a ação.

#### Principais tipos

- **Network DLP (rede):** monitora dados em trânsito na rede corporativa, incluindo tráfego de e-mail e uploads.
- **Endpoint DLP (ponto de extremidade):** aplica políticas em computadores e dispositivos gerenciados, controlando ações como cópia para mídias removíveis ou transferência de arquivos.
- **Cloud DLP (nuvem):** identifica e protege informações armazenadas ou compartilhadas em serviços de nuvem e SaaS.

#### Objetivos

- Reduzir vazamentos acidentais, como o envio de um relatório confidencial ao destinatário errado ou o compartilhamento de informações em serviços não autorizados.
- Ajudar a detectar e impedir usos indevidos por pessoas com acesso legítimo, inclusive ameaças internas.
- Apoiar o cumprimento de leis e normas de proteção de dados, como a LGPD no Brasil e o GDPR na União Europeia.

A eficácia do DLP depende da classificação correta dos dados, de políticas bem definidas e de ajustes que reduzam bloqueios indevidos. Ele complementa, mas não substitui, controles de acesso, treinamento e governança de dados.
