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
## 4. MFA
## 5. Gestão de Identidade e acesso (autenticação, autorização e auditoria), RBAC e ABAC
