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
## 5. Gestão de Identidade e acesso (autenticação, autorização e auditoria), RBAC e ABAC
