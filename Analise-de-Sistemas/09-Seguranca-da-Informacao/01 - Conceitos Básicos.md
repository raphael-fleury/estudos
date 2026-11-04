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

## 2. Operações e métodos de segurança

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

### CASB (Cloud Access Security Broker)

O **CASB (Agente de Segurança de Acesso à Nuvem)** é uma solução que aplica políticas de segurança entre os usuários de uma organização e os serviços em nuvem. Ele amplia a visibilidade e o controle sobre o uso desses serviços, inclusive os que não foram aprovados formalmente pela equipe de TI (*Shadow IT*).

#### Principais funções

- **Visibilidade:** identifica os aplicativos em nuvem utilizados na organização e ajuda a avaliar riscos associados ao *Shadow IT*.
- **Segurança de dados:** aplica políticas de DLP, criptografia e controle de compartilhamento, conforme os recursos disponíveis e a integração configurada.
- **Proteção contra ameaças:** pode identificar atividades suspeitas e ajudar a bloquear malware ou outras ações de risco.
- **Conformidade:** oferece controles, registros e relatórios que apoiam auditorias e o cumprimento de requisitos como os da LGPD e do GDPR.

#### Modelos de implantação

- **Inline (proxy de encaminhamento ou reverso):** inspeciona e aplica políticas ao tráfego entre usuários e serviços em nuvem em tempo real. O efeito depende de como o tráfego é encaminhado pelo CASB.
- **Baseado em API:** integra-se às APIs dos provedores de nuvem para avaliar dados e atividades nos serviços conectados, incluindo dados armazenados (*at rest*). A cobertura e a possibilidade de remediação dependem das APIs e permissões concedidas.

Os modelos inline e baseado em API podem ser usados em conjunto. O CASB complementa controles como DLP e gestão de identidade, mas não substitui a configuração segura dos serviços em nuvem nem a governança de acesso.

### SIEM (Security Information and Event Management)

O **SIEM (Gerenciamento de Informações e Eventos de Segurança)** é uma plataforma que reúne e analisa registros e eventos de segurança de diferentes componentes da infraestrutura de TI. Ao centralizar essas informações, ajuda as equipes de segurança a identificar incidentes e investigar atividades suspeitas.

#### Principais funções

- **Coleta centralizada:** agrega logs e eventos de fontes como firewalls, servidores, roteadores, estações de trabalho e aplicações.
- **Correlação de eventos:** relaciona informações de diferentes fontes para identificar padrões suspeitos que poderiam passar despercebidos quando cada evento é analisado isoladamente.
- **Detecção e alertas:** aplica regras e análises para sinalizar possíveis ameaças e encaminhar alertas à equipe de segurança ou ao SOC (*Security Operations Center*).
- **Investigação e auditoria:** facilita a consulta de eventos e a produção de relatórios que podem apoiar investigações e auditorias.
- **Apoio à conformidade:** contribui para demonstrar controles e manter registros conforme políticas e requisitos aplicáveis, como os relacionados à LGPD, PCI DSS e HIPAA. A conformidade depende também da configuração, da retenção adequada e dos demais controles da organização.

O SIEM apoia a detecção e a investigação, mas não bloqueia necessariamente ameaças por conta própria. A resposta pode depender da análise da equipe e de integrações com ferramentas de automação e proteção.

### Antivírus

O **antivírus** é um software de segurança que procura detectar, bloquear e, quando possível, remover ou colocar em quarentena códigos maliciosos, como vírus, trojans, worms, spyware e ransomware. Pode proteger dispositivos pessoais ou ser gerenciado centralmente em ambientes corporativos.

#### Como funciona

- **Assinaturas:** compara arquivos e códigos com padrões de ameaças conhecidas. A eficácia depende de manter as definições atualizadas.
- **Análise heurística e comportamental:** examina características e ações de programas para identificar atividades suspeitas, inclusive de ameaças ainda não catalogadas. Isso pode ajudar a detectar ameaças novas, mas não garante identificar todos os ataques ou *zero-days*.
- **Proteção em tempo real:** monitora atividades como execução de arquivos, downloads e anexos, podendo bloquear ou sinalizar itens suspeitos antes que causem danos.
- **Verificações sob demanda:** permite examinar arquivos, pastas ou dispositivos em busca de ameaças.

#### Ações e recursos

Quando identifica uma ameaça, o antivírus pode bloquear sua execução, tentar limpar o arquivo ou isolá-lo em quarentena para impedir que interaja com o restante do sistema. Alguns produtos também oferecem recursos adicionais, como proteção contra phishing, firewall ou controle parental; esses recursos variam conforme a solução.

As soluções corporativas permitem administrar a proteção de vários dispositivos por meio de políticas centralizadas. O antivírus é uma camada importante de defesa, mas deve ser mantido atualizado e combinado com controles como atualizações de segurança, cópias de segurança e práticas seguras de uso.

### EDR (Endpoint Detection and Response)

O **EDR (Detecção e Resposta de Ponto de Extremidade)** é uma solução de segurança que monitora continuamente endpoints — como computadores, notebooks, dispositivos móveis e servidores — para identificar, investigar e ajudar a conter ameaças.

#### Principais funções

- **Monitoramento contínuo:** coleta informações sobre atividades nos dispositivos, como processos executados, alterações em arquivos e conexões de rede.
- **Detecção comportamental:** analisa sinais de atividade suspeita que podem indicar ameaças, inclusive comportamentos associados a ransomware ou movimentação lateral.
- **Investigação:** apresenta eventos e contexto sobre atividades detectadas, ajudando a equipe de segurança a entender a sequência e o possível alcance de um incidente.
- **Resposta:** conforme a solução e as políticas configuradas, permite ações manuais ou automatizadas, como isolar um dispositivo da rede, encerrar um processo ou colocar arquivos em quarentena.

#### EDR vs. Antivírus Tradicional (EPP)

- **Antivírus e EPP (Endpoint Protection Platform):** concentram-se em prevenir ameaças, usando recursos como assinaturas e análise comportamental para bloquear atividades maliciosas.
- **EDR:** acrescenta recursos de monitoramento, detecção, investigação e resposta a incidentes nos endpoints.

Essas capacidades podem coexistir em uma mesma plataforma. O EDR complementa a prevenção, mas não garante que toda ameaça seja detectada ou contida; sua eficácia depende da cobertura dos dispositivos, das políticas e da resposta da equipe.

### WAF (Web Application Firewall)

O **WAF (Web Application Firewall ou Firewall de Aplicativo Web)** é uma solução de segurança que filtra, monitora e pode bloquear o tráfego HTTP/HTTPS de e para um site, sistema ou API.

#### Como funciona

- **Camada de aplicação:** diferente de um firewall tradicional, que controla o tráfego de rede de forma mais ampla, o WAF atua na camada 7 do modelo OSI (Camada de Aplicação) e inspeciona requisições web antes que elas cheguem à aplicação.
- **Filtros e regras:** pode operar com listas de bloqueio, listas de permissão ou modelos híbridos. Algumas soluções também usam análise comportamental e técnicas de inteligência artificial para identificar atividades anômalas.
- **Tipos de implantação:**
  - **Baseado em nuvem:** geralmente é simples de configurar e pode ser integrado por meio de alterações de DNS.
  - **Baseado em rede (hardware):** instalado localmente, pode oferecer baixa latência, mas costuma ter maior custo de aquisição e manutenção.
  - **Baseado em host (software):** executado no servidor ou integrado ao ambiente da aplicação.

#### Principais ameaças que ajuda a combater

- **Injeção de SQL (SQLi):** tentativas de manipular consultas ao banco de dados por meio de entradas da aplicação.
- **Cross-Site Scripting (XSS):** tentativas de inserir scripts que podem ser executados nos navegadores de outros usuários.
- **Negação de serviço na camada 7:** volume de solicitações que busca sobrecarregar uma aplicação web.
- **Exploração de vulnerabilidades e bots maliciosos:** solicitações automatizadas ou suspeitas dirigidas à aplicação.

Um WAF complementa, mas não substitui, práticas de desenvolvimento seguro, correção de vulnerabilidades e outros controles de segurança. Sua eficácia depende das regras, da configuração e da atualização contínua.

### Gestão de vulnerabilidades

A **gestão de vulnerabilidades** é o processo contínuo e estruturado de identificar, avaliar, priorizar, corrigir e monitorar falhas de segurança em sistemas, redes, softwares e infraestruturas antes que agentes maliciosos consigam explorá-las.

O objetivo principal é reduzir a **janela de exposição** — o tempo entre a descoberta de uma falha e a sua correção — e diminuir a superfície de ataque da organização.

#### Principais etapas do ciclo de vida

1. **Descoberta e inventário:** mapear os ativos da organização, incluindo hardware, softwares, recursos em nuvem, contêineres e dispositivos, para saber o que precisa ser protegido.
2. **Avaliação e categorização:** utilizar scanners de vulnerabilidade e referências padronizadas, como CVE, NVD e pontuações CVSS, para identificar e avaliar as falhas encontradas.
3. **Priorização baseada em risco (RBVM):** priorizar as correções conforme o risco real para o negócio, em vez de tentar corrigir todas as falhas ao mesmo tempo. Métricas como EPSS, que estima a probabilidade de exploração, e KEV, que identifica vulnerabilidades exploradas ativamente, podem apoiar essa decisão.
4. **Resolução ou remediação:** aplicar patches (atualizações), corrigir configurações ou implementar mitigações temporárias.
5. **Reavaliação e relatório:** realizar novas varreduras para confirmar se as falhas foram eliminadas e acompanhar indicadores de desempenho, como o MTTR (tempo médio de resolução).

### Monitoramento de segurança da informação

O **monitoramento de segurança da informação** é a observação contínua de redes, sistemas, servidores e comportamentos digitais para identificar ameaças, vulnerabilidades e atividades suspeitas em tempo hábil.

#### O que envolve o monitoramento?

- **Análise de logs e eventos:** registrar e processar dados sobre quem acessou quais recursos, quando e de onde.
- **Visibilidade do ambiente:** identificar falhas de configuração, tráfego anômalo e tentativas de ataque, como phishing ou disseminação de malware.
- **Detecção precoce:** alertar rapidamente as equipes de TI ou os Centros de Operações de Segurança (SOC), para que possam agir antes que um incidente cause danos graves.
- **Conformidade regulatória:** apoiar o cumprimento de requisitos legais e regulatórios, incluindo os relacionados à proteção de dados, como a LGPD.

### Backup (cópia de segurança)

O **backup** é o processo de criar cópias de segurança de arquivos, sistemas ou bancos de dados e armazená-las separadamente dos dados originais. É um pilar da segurança da informação, pois ajuda a recuperar dados após falhas de hardware, erros humanos, ataques como ransomware ou desastres naturais.

#### Estratégia 3-2-1

Uma prática recomendada para aumentar a resiliência dos backups é a estratégia 3-2-1:

- **3 cópias:** mantenha pelo menos três cópias dos dados, contando a original e duas cópias de segurança.
- **2 tipos de mídia:** armazene as cópias em pelo menos dois tipos de mídia ou sistemas diferentes, como armazenamento local e nuvem.
- **1 cópia fora do local:** mantenha pelo menos uma cópia em uma localização física ou lógica separada, que pode ser um serviço em nuvem.

#### Tipos de backup

- **Completo (full):** copia todos os dados selecionados. É simples de restaurar, mas normalmente exige mais tempo e espaço de armazenamento.
- **Incremental:** copia os dados alterados ou criados desde o backup anterior, seja ele completo ou incremental. Costuma ser rápido e ocupar menos espaço, mas a restauração pode exigir o backup completo e vários incrementais.
- **Diferencial:** copia os dados alterados ou criados desde o último backup completo. Em geral, ocupa mais espaço que o incremental, mas a restauração requer o backup completo e o diferencial mais recente.

#### Boas práticas de segurança

- **Criptografia:** proteja os backups com criptografia para reduzir o risco de exposição caso a mídia seja perdida, roubada ou acessada indevidamente.
- **Isolamento:** mantenha algumas cópias desconectadas da rede principal ou protegidas contra alterações, para dificultar que um ransomware também as comprometa.
- **Testes de restauração:** teste periodicamente a recuperação dos dados para verificar se as cópias estão íntegras e se podem ser restauradas dentro do tempo necessário.
- **Controle de acesso:** restrinja e monitore quem pode acessar, alterar ou excluir os backups.
