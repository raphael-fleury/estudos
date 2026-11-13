# Ameaças e Ataques

## 1. Softwares maliciosos (*malware*)

### Ransomware

Sequestra dados confidenciais ou bloqueia o acesso a dispositivos (computadores, servidores e redes), exigindo o pagamento de um resgate (geralmente em criptomoedas como Bitcoin) para a liberação ou descriptografia das informações.

### Vírus

São projetados para se infiltrar em um sistema, anexar-se a arquivos ou programas legítimos e fazer cópias de si mesmo (autorreprodução) para espalhar a infecção a outros arquivos e computadores.

Quase sempre depende de uma ação do usuário para ser ativado — como abrir um anexo de e-mail malicioso, executar um programa baixado da internet ou clicar em um arquivo corrompido.

### Worms

Se replica e se espalha automaticamente por redes de computadores sem precisar de intervenção humana ou de um arquivo hospedeiro.

### Spyware

Projetado para se infiltrar em computadores, celulares ou tablets sem o consentimento do usuário, com o objetivo de monitorar atividades e roubar dados confidenciais.

#### Principais tipos de spyware

- **Keyloggers:** Registram as teclas digitadas, podendo capturar senhas, números de cartão de crédito e mensagens.
- **Infostealers (roubadores de dados):** Coletam senhas salvas, histórico de navegação, cookies, e-mails e arquivos do sistema.
- **Trojans bancários:** Falsificam telas de acesso a bancos ou interceptam transações financeiras.
- **Stalkerware:** Aplicativos instalados para rastrear a localização GPS, ligações, fotos e mensagens de um indivíduo; são muitas vezes usados em relações abusivas.
- **Pegasus e spywares governamentais:** Softwares avançados, frequentemente com capacidade de infecção *zero-click*, usados para espionar alvos específicos, como jornalistas e políticos.

### Rootkit

É um conjunto de ferramentas de software (geralmente maliciosas) projetadas para obter e manter acesso privilegiado de nível de administrador ("root" ou superusuário) em um sistema, ocultando a própria presença e a de outros malwares.

Por operarem em níveis profundos do sistema (muitas vezes no kernel), muitos antivírus tradicionais têm dificuldade para localizá-los.

## 2. Ataques

### DDoS

Um ataque DDoS (*Distributed Denial of Service*, ou **Ataque Distribuído de Negação de Serviço**) é uma tentativa maliciosa de derrubar um site, servidor ou serviço online, sobrecarregando-o com um volume excessivo de acessos e solicitações

### SQL Injection

Explora vulnerabilidades no código de um aplicativo inserindo uma consulta SQL em campos regulares de entrada ou formulário.

### XSS

O Cross-Site Scripting (XSS) é uma vulnerabilidade de segurança em aplicações web que permite a invasores injetar códigos maliciosos (geralmente JavaScript) em páginas vistas por outros usuários. O navegador da vítima executa esse script confiando que ele pertence ao site legítimo, o que pode resultar no roubo de cookies, sessões ou dados sensíveis.

### CSRF

Cross-Site Request Forgery (CSRF) é um tipo de ataque em que um site malicioso faz com que o navegador de um usuário autenticado execute ações indesejadas em outra aplicação web na qual ele está logado (como fazer uma transferência bancária ou alterar uma senha).

### Path Traversal

O Path Traversal (também conhecido como *Directory Traversal* ou ataque ponto-ponto-barra) é uma vulnerabilidade de segurança que permite a invasores ler arquivos e diretórios confidenciais armazenados fora da pasta raiz da aplicação web.