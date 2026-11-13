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

### Botnet

Rede de computadores infectados que são controlados remotamente por um atacante (denominado "bot master"). Os computadores infectados são conhecidos como "bots" ou "zumbis" e podem ser coordenados para executar ações maliciosas em massa, como enviar spam, realizar ataques DDoS ou roubar dados.

### Adware

Software que exibe propagandas indesejadas, frequentemente de forma agressiva e intrusiva. Além disso, coleta dados de navegação e hábitos de navegação do usuário para fins de marketing direcionado. Geralmente é distribuído junto com outros softwares aparentemente legítimos.

### Cryptojacking

Malware que se infiltra em computadores ou dispositivos móveis e utiliza seus recursos de processamento (CPU, GPU) para minerar criptomoedas (como Bitcoin ou Monero) sem o conhecimento ou consentimento do usuário. Consome recursos do sistema e degrada o desempenho.

### PUPs (Potentially Unwanted Programs)

Programas potencialmente indesejados que não são necessariamente maliciosos, mas são instalados sem consentimento explícito do usuário, frequentemente em conjunto com software legítimo. Incluem barras de ferramentas não solicitadas, extensões de navegador e modificadores de página inicial.

### Fileless Malware

Malware sofisticado que funciona apenas na memória RAM do sistema, sem deixar arquivos em disco rígido. Isso o torna mais difícil de detectar pelos antivírus tradicionais, pois não deixa rastros permanentes e desaparece ao reiniciar o computador. Frequentemente explora funcionalidades legítimas do sistema operacional.

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

### Phishing e Spearphishing

**Phishing** é um ataque de engenharia social em que o atacante envia mensagens (geralmente emails) fingindo ser de uma fonte confiável para enganar o usuário e fazer com que revele informações sensíveis (como senhas, dados bancários ou números de cartão de crédito).

**Spearphishing** é uma variante mais direcionada que visa indivíduos ou organizações específicas, personalizando a mensagem com informações sobre a vítima para aumentar a credibilidade do ataque.

### Man-in-the-Middle (MitM)

Um atacante se posiciona entre dois pontos de comunicação (cliente e servidor) e intercepta, observa ou altera dados em trânsito. Pode capturar credenciais, dados sensíveis, ou injetar conteúdo malicioso. Frequentemente explorado em redes Wi-Fi públicas desprotegidas.

### Brute Force

Ataque que tenta descobrir uma senha, chave de criptografia ou token através de tentativas sistemáticas e repetidas até encontrar a combinação correta. É particularmente eficaz contra senhas fracas e pode ser automatizado para testar milhões de possibilidades rapidamente.

### Privilege Escalation

Técnica na qual um atacante com acesso limitado a um sistema consegue elevar seus privilégios para obter acesso de nível administrativo ou de root. Explora vulnerabilidades no sistema operacional ou aplicações para executar com permissões maiores.

### Zero-Day Exploit

Exploração de uma vulnerabilidade de segurança desconhecida pelos proprietários do software (ainda não há um patch disponível). O atacante possui conhecimento exclusivo da falha e pode explorá-la livremente até que o desenvolvedor publique uma correção.

### Social Engineering

Técnica de manipulação psicológica que tira proveito da natureza humana para enganar pessoas e obter acesso a informações sensíveis, sistemas ou edifícios. Pode envolver pretexto, engano emocional ou exploração da confiança entre indivíduos.

### API Abuse

Uso malicioso de Application Programming Interfaces (APIs) para extrair dados em massa, derrubar serviços através de requisições excessivas, ou contornar controles de segurança. Frequentemente realizado através de automação para escalar a taxa de requisições.

### Race Condition

Vulnerabilidade que ocorre quando o resultado de uma operação depende da sequência ou timing de eventos não sincronizados. Um atacante pode explorar o período entre duas operações para executar código malicioso ou acessar dados em estado inconsistente.

### XXE (XML External Entity)

Vulnerabilidade que permite injetar entidades XML maliciosas em uma aplicação que processa XML. Pode levar ao roubo de dados confidenciais, acesso a arquivos internos, ou ataques de negação de serviço (DoS).

### Insecure Deserialization

Vulnerabilidade que ocorre quando uma aplicação desserializa dados não confiáveis sem validação adequada. Um atacante pode enviar dados serializados maliciosos que executam código arbitrário no sistema quando desserializados.

### SSRF (Server-Side Request Forgery)

Vulnerabilidade que permite a um atacante fazer o servidor executar requisições HTTP não autorizadas em seu nome. Pode ser usado para acessar sistemas internos, fazer requests a URLs privadas, ou contornar firewalls internos da aplicação.

### LDAP Injection

Semelhante à SQL Injection, permite a injeção de comandos LDAP maliciosos em campos de entrada. Explorada contra sistemas que usam LDAP para autenticação, pode permitir bypass de autenticação ou extração de informações sensíveis.