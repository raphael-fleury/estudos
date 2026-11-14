# Acesso e Autenticação

## 1. VPN

Uma **VPN (Rede Privada Virtual)** cria um túnel criptografado entre um dispositivo e um servidor VPN, protegendo o tráfego durante esse trecho da comunicação.

### Como funciona

- **Criptografia de dados:** os dados enviados pelo dispositivo são criptografados antes de trafegarem pela internet até o servidor VPN.
- **Mascaramento de IP:** para os serviços acessados, o endereço IP visível é geralmente o do servidor VPN, em vez do IP público do dispositivo.
- **Proteção em redes públicas:** o túnel dificulta que pessoas na mesma rede Wi-Fi aberta interceptem o tráfego protegido, como o de cafés, hotéis ou aeroportos.
- **Acesso corporativo:** permite que funcionários se conectem com segurança a sistemas e arquivos internos da empresa, mesmo estando fora do escritório.

> **Atenção:** a VPN protege o tráfego entre o dispositivo e o servidor VPN; ela não garante anonimato nem substitui HTTPS, antivírus ou outras medidas de segurança. A proteção de todo o tráfego também depende da configuração da VPN.

## 2. MDM

**MDM (Mobile Device Management ou Gerenciamento de Dispositivos Móveis)** é uma solução de tecnologia e segurança da informação que permite à equipe de TI monitorar, gerenciar e proteger smartphones, tablets e notebooks a partir de um console centralizado.

### Funções principais na Segurança da Informação

- **Apagamento e bloqueio remoto (*Remote Wipe*):** em caso de perda, roubo ou desligamento de um funcionário, a equipe de TI pode bloquear o dispositivo ou apagar os dados corporativos à distância para reduzir o risco de vazamento.
- **Contêinerização (*Containerization*):** separa os dados e aplicativos da empresa dos dados pessoais do usuário, prática comum em políticas de BYOD (*Bring Your Own Device*).
- **Criptografia e senhas fortes:** aplica requisitos de senha ou PIN e configurações de criptografia no dispositivo.
- **Controle de aplicativos:** gerencia quais aplicativos podem ser instalados ou usados, ajudando a bloquear softwares maliciosos ou não autorizados.
- **Conformidade regulatória:** auxilia na adequação a normas de proteção de dados, como a LGPD, por meio de controles, rastreabilidade e proteção das informações.

### Soluções conhecidas

- Microsoft Intune
- Jamf Pro / Jamf School
- SOTI MobiControl

## 3. SSO

**Single Sign-On (SSO)** é um método de autenticação que permite ao usuário fazer login uma vez e obter acesso a vários aplicativos e sistemas conectados, sem precisar inserir as credenciais novamente em cada um.

### Como funciona

1. **Provedor de Identidade (*Identity Provider*, IdP):** sistema central, como Microsoft Entra ID, Okta ou Keycloak, que autentica o usuário e emite informações sobre sua identidade.
2. **Provedor de Serviço (*Service Provider*, SP):** aplicativo ou site que o usuário deseja acessar, como Slack, e-mail corporativo ou Salesforce.
3. **Troca de informações de autenticação:** após o login no IdP, o usuário recebe uma resposta ou token de autenticação que o aplicativo pode validar. A troca pode usar SAML ou OpenID Connect; OAuth 2.0 é principalmente um protocolo de autorização e costuma ser combinado com OpenID Connect para autenticação.

### Benefícios para a Segurança da Informação

- **Redução da fadiga de senhas:** diminui a necessidade de criar e lembrar dezenas de senhas, reduzindo a tentação de reutilizá-las.
- **Menos chamados de suporte:** pode reduzir pedidos de redefinição de senha ao departamento de TI ou *Help Desk*.
- **Gestão centralizada de acessos:** facilita conceder ou revogar acessos aos sistemas conectados, por exemplo, quando um funcionário deixa a empresa. A revogação efetiva também depende da configuração das sessões e dos aplicativos.
- **Integração com MFA (Autenticação Multifator):** permite exigir MFA no IdP durante o login e aplicar essa proteção aos aplicativos integrados ao SSO.

### Riscos e cuidados

- **Ponto único de falha:** se a conta do IdP for comprometida, os sistemas vinculados podem ficar expostos.
- **Mitigação:** exigir MFA resistente a phishing sempre que possível, aplicar políticas de acesso condicional e monitorar continuamente logins e sessões.

## 4. MFA

**MFA (Autenticação Multifator)** é um processo de segurança que exige duas ou mais formas diferentes de verificação para confirmar a identidade de um usuário antes de liberar o acesso a um sistema, conta ou aplicativo. Para ser multifator, as verificações devem pertencer a categorias distintas.

### Como funciona

A autenticação combina fatores de diferentes categorias:

- **Algo que você sabe:** senha, PIN ou resposta a uma pergunta secreta.
- **Algo que você tem:** smartphone com aplicativo autenticador, token físico, chave de segurança ou código enviado por SMS.
- **Algo que você é:** característica biométrica, como impressão digital, reconhecimento facial ou leitura de íris.

> **Atenção:** códigos por SMS podem ser vulneráveis a golpes de troca de chip e interceptação. Sempre que possível, prefira chaves de segurança ou outros métodos resistentes a phishing.

### Importância da MFA

- **Proteção contra roubo de senhas:** uma senha comprometida, por phishing ou vazamento, não costuma ser suficiente para acessar a conta quando um segundo fator é exigido.
- **Redução de riscos:** dificulta muitas tentativas automatizadas e ataques de força bruta, mas não elimina todos os riscos, especialmente quando o próprio segundo fator pode ser enganado ou roubado.
- **Camadas de defesa:** adiciona uma barreira de segurança recomendada em políticas corporativas e boas práticas de proteção de dados.

## 5. Gestão de Identidade e acesso (autenticação, autorização e auditoria), RBAC e ABAC

A **Gestão de Identidade e Acesso (IAM — *Identity and Access Management*)** reúne políticas e tecnologias para garantir que as pessoas certas tenham acesso aos recursos adequados, no momento e pelos motivos apropriados. Ela organiza o ciclo de vida das identidades e os privilégios associados, apoiando-se nos três pilares operacionais conhecidos como **AAA** e em modelos de controle de acesso, como RBAC e ABAC.

### Os três pilares do acesso (AAA)

O AAA divide o controle de acesso em três funções complementares:

1. **Autenticação (*Authentication*):** verifica a identidade declarada pelo usuário, por exemplo, com senha, MFA ou biometria.
2. **Autorização (*Authorization*):** determina quais recursos e ações a identidade autenticada pode acessar, conforme as permissões e políticas aplicáveis.
3. **Auditoria (*Accounting*):** registra atividades e eventos de acesso, permitindo rastreabilidade, análise e investigação. Nesse contexto, *accounting* refere-se ao registro de uso, não necessariamente à cobrança.

### Modelos de controle de acesso: RBAC e ABAC

Na etapa de autorização, modelos estruturados ajudam a gerenciar permissões em escala. Os dois principais são RBAC e ABAC:

| Critério | RBAC (*Role-Based Access Control*) | ABAC (*Attribute-Based Access Control*) |
| --- | --- | --- |
| **Base da decisão** | Papéis ou funções atribuídos ao usuário, como gerente, analista ou administrador. | Atributos do usuário, do recurso, da ação e do ambiente. |
| **Granularidade** | Em geral, média ou baixa: permissões agrupadas em papéis predefinidos. | Alta: permite regras específicas e contextuais. |
| **Contexto em tempo real** | Por padrão, não considera fatores externos como horário, localização ou dispositivo; pode ser combinado com outros controles. | Pode avaliar o contexto da solicitação, como permitir acesso apenas em horário comercial e na rede interna. |
| **Complexidade** | Mais simples de implementar e administrar em estruturas organizacionais estáveis. | Mais complexo de projetar e exige governança rigorosa dos atributos e de sua atualização. |
| **Principal desafio** | **Explosão de papéis** (*role explosion*): criação excessiva de papéis para atender a exceções. | Manutenção de políticas complexas e dependência de atributos corretos e atualizados. |

### RBAC (*Role-Based Access Control*)

O **RBAC (Controle de Acesso Baseado em Funções)** restringe o acesso aos recursos conforme as funções atribuídas aos usuários na organização, em vez de configurar permissões individualmente para cada pessoa. O administrador define as permissões de cada função e atribui os usuários às funções adequadas.

#### Componentes principais

- **Usuário:** pessoa ou entidade que precisa acessar o sistema.
- **Função (*role*):** conjunto de responsabilidades e permissões, como Financeiro, RH ou Suporte.
- **Permissão:** autorização para executar uma ação específica, como ler, criar, editar ou excluir um arquivo.
- **Sessão:** contexto de acesso ativo em que o usuário utiliza uma ou mais de suas funções.

#### Vantagens para a segurança

- **Princípio do privilégio mínimo:** facilita conceder apenas as permissões necessárias ao trabalho, desde que as funções sejam bem definidas e revisadas.
- **Limitação do impacto de uma conta comprometida:** restringir cada função ao acesso necessário pode reduzir os recursos disponíveis a um invasor que comprometa uma conta.
- **Facilidade de gestão:** mudanças de cargo ou desligamentos podem ser tratados ajustando ou removendo as funções atribuídas, em vez de alterar permissões uma a uma.
- **Conformidade e auditoria:** a associação entre usuários, funções e permissões facilita verificar quem pode acessar cada recurso.

### ABAC (*Attribute-Based Access Control*)

O **ABAC (Controle de Acesso Baseado em Atributos)** é um modelo de autorização que concede ou nega acesso a recursos com base na combinação de atributos e condições dinâmicas, em vez de depender apenas de papéis fixos, como no RBAC. Uma política avalia as condições da solicitação e decide se a ação é permitida.

#### Componentes principais

As decisões de acesso podem combinar quatro categorias de atributos:

1. **Sujeito (usuário):** quem está tentando acessar, como cargo, departamento, nível de liberação ou identificador.
2. **Recurso (objeto):** o que está sendo acessado, como tipo de arquivo, proprietário, data de criação ou nível de confidencialidade.
3. **Ação:** o que o usuário pretende fazer, como ler, escrever, editar ou excluir.
4. **Ambiente:** o contexto da solicitação, como horário, localização ou IP, tipo de dispositivo e rede segura ou pública.

#### Exemplo prático

> Permitir que um funcionário do departamento financeiro edite planilhas de folha de pagamento somente quando estiver na rede corporativa e durante o horário comercial, das 9h às 18h.

Nesse caso, a política verifica o departamento do usuário, a ação solicitada, o recurso, a rede e o horário antes de permitir ou negar o acesso.


