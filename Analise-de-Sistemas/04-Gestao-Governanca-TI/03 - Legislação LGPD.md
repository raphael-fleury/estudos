# Legislação e LGPD

## 1. Lei Geral de Proteção de Dados Pessoais

A **Lei nº 13.709/2018 (LGPD)** regula o tratamento de dados pessoais por pessoas físicas ou jurídicas, públicas ou privadas. Aplica-se a operações realizadas no Brasil, a dados coletados no Brasil ou a atividades que ofereçam bens/serviços a pessoas localizadas no país, conforme os critérios territoriais da lei. Abrange meios digitais e físicos.

Esta nota é uma referência técnica, não substitui orientação jurídica. O desenvolvedor implementa requisitos e controles definidos com o **controlador**, o encarregado e as áreas de segurança/privacidade; não deve escolher sozinho a finalidade, a base legal ou o prazo de retenção.

## 2. Conceitos que orientam o projeto

- **Dado pessoal:** informação relacionada a pessoa natural identificada ou identificável. Identificadores diretos (nome, CPF, e-mail) e combinações de dados, identificadores online, localização ou histórico podem identificar alguém.
- **Dado pessoal sensível:** dado sobre origem racial ou étnica, convicção religiosa, opinião política, filiação a sindicato ou organização religiosa/filosófica/política, saúde, vida sexual, dado genético ou biométrico vinculado a uma pessoa.
- **Dado anonimizado:** dado que não permite identificar o titular por meios técnicos razoáveis e disponíveis. Se a reversão for razoavelmente possível, ou se a identificação puder ocorrer por cruzamento, não trate o dado como anônimo. **Pseudonimização** reduz a associação direta, mas o dado continua sendo pessoal se puder ser reidentificado.
- **Tratamento:** qualquer operação com dados pessoais, como coleta, consulta, uso, classificação, armazenamento, compartilhamento, alteração, eliminação ou avaliação.
- **Titular:** pessoa natural a quem os dados se referem.
- **Controlador:** decide as finalidades e os elementos essenciais do tratamento.
- **Operador:** trata dados em nome do controlador e conforme suas instruções. Um fornecedor não é automaticamente operador em todos os contextos; os papéis dependem de quem efetivamente decide e executa cada tratamento.
- **Encarregado (DPO):** canal de comunicação entre controlador, titulares e ANPD. A obrigação e as regras aplicáveis dependem da regulamentação da ANPD e do tipo de agente.
- **ANPD:** Autoridade Nacional de Proteção de Dados, responsável por orientar, regulamentar e fiscalizar a aplicação da lei.

Dados de crianças e adolescentes exigem atenção especial: o tratamento deve observar seu melhor interesse e as regras específicas da LGPD, inclusive requisitos de consentimento quando aplicáveis.

## 3. Princípios a traduzir em requisitos de software

Todo tratamento deve respeitar, entre outros, os princípios de:

1. **Finalidade:** propósito legítimo, específico, explícito e informado; não reutilizar os dados de modo incompatível.
2. **Adequação:** compatibilidade do tratamento com a finalidade comunicada.
3. **Necessidade:** limitar dados ao mínimo pertinente e não excessivo.
4. **Livre acesso e qualidade:** permitir consulta facilitada e dados corretos, claros, relevantes e atualizados.
5. **Transparência:** explicar ao titular, com clareza, o tratamento e os agentes envolvidos.
6. **Segurança e prevenção:** proteger contra acesso não autorizado, perda, alteração, divulgação ou tratamento inadequado, e prevenir danos.
7. **Não discriminação:** não usar dados para fins discriminatórios ilícitos ou abusivos.
8. **Responsabilização e prestação de contas:** demonstrar que medidas eficazes foram adotadas e funcionam.

Na prática, documente **quais dados** são tratados, **por quê**, **com qual base legal**, **por quanto tempo**, **por quem** e **com quem são compartilhados**. Uma nova finalidade, campo, integração, rastreador ou modelo analítico deve passar por avaliação de privacidade antes de entrar em produção.

## 4. Bases legais: não presumir que tudo depende de consentimento

O controlador deve identificar e documentar uma base legal adequada para cada finalidade, antes do tratamento. As bases do art. 7º incluem:

- consentimento do titular;
- cumprimento de obrigação legal ou regulatória;
- execução de políticas públicas pela administração pública;
- estudos por órgão de pesquisa, com anonimização sempre que possível;
- execução de contrato ou procedimentos preliminares solicitados pelo titular;
- exercício regular de direitos em processo judicial, administrativo ou arbitral;
- proteção da vida ou da incolumidade física;
- tutela da saúde, nas condições previstas em lei;
- legítimo interesse do controlador ou de terceiro, respeitados os direitos do titular e os limites legais;
- proteção do crédito.

Para **dados sensíveis**, aplicam-se as hipóteses específicas do art. 11: por exemplo, consentimento específico e destacado para finalidades específicas ou, sem consentimento, uma das hipóteses legais próprias (como obrigação legal, políticas públicas, pesquisa, exercício de direitos, proteção da vida, tutela da saúde ou prevenção à fraude/segurança nos limites legais). Não basta reutilizar automaticamente uma base do art. 7º.

Cuidados importantes:

- Consentimento deve ser livre, informado, inequívoco e relacionado a finalidades determinadas. Quando necessário, deve ser destacado; autorizações genéricas são inválidas. O titular pode revogá-lo por procedimento gratuito e facilitado.
- Não use consentimento como solução padrão quando outra base for a correta ou quando não houver escolha real. A retirada do consentimento não elimina tratamentos anteriores lícitos nem obrigações legais de retenção.
- Legítimo interesse **não é base para dados sensíveis**. Seu uso requer finalidade legítima concreta, necessidade, consideração das expectativas e dos direitos do titular e salvaguardas; documente a avaliação com o controlador/privacidade.
- Dados tornados públicos pelo titular continuam sujeitos à LGPD e aos princípios, direitos e finalidade compatível. Acesso público não significa autorização irrestrita para qualquer reutilização.
- Registre a base legal por finalidade e mantenha coerência entre inventário, avisos de privacidade, contratos, código e operação.

## 5. Direitos dos titulares e impactos na aplicação

O sistema e os processos de atendimento devem viabilizar, conforme aplicável, pedidos para:

- confirmar a existência de tratamento e obter acesso aos dados;
- corrigir dados incompletos, inexatos ou desatualizados;
- anonimizar, bloquear ou eliminar dados desnecessários, excessivos ou tratados em desconformidade;
- solicitar portabilidade, observada a regulamentação da ANPD e os segredos comercial e industrial;
- eliminar dados tratados com consentimento, ressalvadas as hipóteses legais de conservação;
- obter informação sobre entidades públicas e privadas com as quais houve uso compartilhado;
- receber informação sobre a possibilidade de negar consentimento e suas consequências;
- revogar consentimento;
- opor-se a tratamento realizado sem consentimento quando houver descumprimento da lei;
- solicitar revisão de decisões tomadas unicamente com base em tratamento automatizado que afetem seus interesses e obter informações claras sobre critérios e procedimentos, resguardados os segredos comerciais.

Implicações de implementação:

- Tenha fluxo para localizar os dados de um titular em bancos, réplicas, índices, data lakes, sistemas de terceiros e, quando aplicável, cópias de segurança.
- Confirme identidade proporcionalmente ao risco, sem coletar novos dados excessivos para responder ao pedido.
- Separe dados que devem ser apagados dos que precisam ser conservados por obrigação legal ou outra hipótese autorizada; documente o motivo e restrinja o uso durante a retenção.
- Propague correções e exclusões aos destinatários quando exigido, e mantenha trilha de auditoria sem perpetuar o dado removido em logs.
- A LGPD prevê resposta simplificada imediata ou declaração clara e completa no prazo legal de até **15 dias** para confirmação/acesso, nos termos do art. 19. O fluxo operacional deve ser validado pelo controlador e observar regras específicas aplicáveis.

## 6. Checklist para desenvolvedores

### Antes de desenvolver

- Faça inventário/fluxo de dados: origem, finalidade, titulares, campos, base legal, destinatários, localização, retenção e descarte.
- Questione cada campo: é necessário? Pode ser opcional, agregado ou anonimizado? Evite coletar “por precaução”.
- Classifique dados pessoais e sensíveis; restrinja o acesso por função e necessidade de negócio.
- Avalie riscos e envolva privacidade/segurança desde o desenho. Operações de maior risco podem exigir **Relatório de Impacto à Proteção de Dados Pessoais (RIPD)**; sua necessidade deve ser decidida com o controlador e pode ser exigida pela ANPD.
- Defina responsabilidades e instruções para fornecedores, bibliotecas, serviços em nuvem, analytics, suporte e suboperadores. Contratos e configurações devem refletir o papel real de cada parte.

### Durante o desenvolvimento e a operação

- Adote **privacidade desde a concepção e por padrão**: configurações mais protetivas, acesso mínimo, retenção limitada e compartilhamento desativado até ser necessário.
- Proteja dados em trânsito e em repouso com medidas adequadas; use gestão segura de segredos, autenticação forte, autorização, segregação de ambientes, atualização de dependências, backups protegidos e monitoramento.
- Não inclua dados pessoais em logs, mensagens de erro, métricas, URLs, ferramentas de observabilidade, tickets ou dados de teste sem necessidade e controles. Prefira dados sintéticos; mascare ou pseudonimize quando apropriado.
- Trate consentimento e preferências de forma verificável e específica por finalidade. Guarde evidências necessárias (versão do aviso, finalidade, data e ação) sem coletar evidência excessiva.
- Implemente retenção e descarte automatizados conforme política aprovada. “Guardar para sempre” não é padrão seguro; bloqueie acessos e elimine ou anonimize quando a finalidade terminar, salvo hipótese legal de conservação.
- Proteja exportações e integrações, limite consultas em massa, valide destinatários e evite exposição de dados em interfaces, cache, relatórios ou notificações.
- Documente mudanças de finalidade, novos campos, novos destinatários e incidentes. Faça revisão de acesso, testes de segurança e exercícios dos fluxos de direitos.
- Avalie transferências internacionais antes de usar serviços ou armazenar dados fora do Brasil. A transferência deve se enquadrar em mecanismo autorizado pela LGPD e pela regulamentação da ANPD; cláusulas contratuais padrão e demais salvaguardas podem ser necessárias.
- Cookies, SDKs e identificadores de publicidade/analytics também podem envolver dados pessoais. Mapeie finalidade, base legal, terceiros e controles; respeite as escolhas válidas do titular e não use banner como substituto de uma análise jurídica.
- Para decisões automatizadas/IA, avalie dados de entrada, finalidade, necessidade, qualidade, vieses, impactos, explicabilidade possível, revisão e exercício de direitos. Não envie dados pessoais a ferramentas externas sem autorização e avaliação de privacidade/segurança.

## 7. Incidentes de segurança

Incidente que envolva dados pessoais deve ser escalado imediatamente pelo desenvolvedor à equipe responsável, mesmo antes de estar totalmente investigado. Preserve evidências e registre quando foi detectado, sistemas e dados potencialmente afetados, titulares, medidas de contenção e decisões tomadas. Não comunique titulares ou a ANPD por conta própria sem o fluxo definido pelo controlador.

Pelo art. 48, cabe ao **controlador** comunicar à ANPD e aos titulares incidentes que possam acarretar risco ou dano relevante. O Regulamento de Comunicação de Incidente de Segurança da ANPD (Resolução CD/ANPD nº 15/2024) estabelece, como regra geral, prazo de **três dias úteis** a partir do conhecimento pelo controlador, com condições e exceções previstas no regulamento. O operador deve informar o controlador sem demora injustificada, conforme instruções e contrato, para que o prazo possa ser cumprido. A comunicação ao titular deve ser clara e conter as informações regulamentares; incidentes e providências devem ser documentados.

Não espere pela certeza de exfiltração para escalar. O time técnico deve viabilizar contenção, investigação, avaliação de risco e correção; a decisão de comunicar é do controlador, com apoio jurídico/privacidade e segurança.

## 8. Responsabilização e sanções

O controlador e o operador podem responder por danos patrimoniais, morais, individuais ou coletivos nos termos da LGPD. A ANPD pode aplicar, conforme o caso e o processo legal, advertência, multa simples de até **2% do faturamento no Brasil** do grupo ou conglomerado no último exercício, excluídos tributos e limitada a **R$ 50 milhões por infração**, multa diária, publicização da infração, bloqueio ou eliminação de dados, suspensão parcial do banco/atividade e proibição parcial ou total de atividades relacionadas ao tratamento. As sanções e limites variam conforme o agente e a situação.

A conformidade não é apenas política ou aviso de privacidade: é preciso demonstrar controles, decisões, contratos, registros e resposta efetiva.

## 9. Referências oficiais

- [Lei nº 13.709/2018 — texto compilado, Portal Planalto](https://www.planalto.gov.br/ccivil_03/_ato2015-2018/2018/lei/l13709.htm)
- [ANPD — Comunicação de incidente de segurança](https://www.gov.br/anpd/pt-br/canais_atendimento/agente-de-tratamento/comunicado-de-incidente-de-seguranca-cis)
- [Resolução CD/ANPD nº 15/2024 — Regulamento de Comunicação de Incidente de Segurança](https://www.in.gov.br/en/web/dou/-/resolucao-cd/anpd-n-15-de-24-de-abril-de-2024-556243024)
- [ANPD — Assuntos internacionais e transferência de dados](https://www.gov.br/anpd/pt-br/assuntos/assuntos-internacionais)
- [Portal da ANPD — legislação, guias e regulamentos](https://www.gov.br/anpd/pt-br)

Regulamentos e orientações podem mudar; confira a versão vigente das fontes oficiais e as regras setoriais aplicáveis ao projeto.
