# Desenvolvimento Seguro

## 1. Técnicas de desenvolvimento seguro, SAST/DAST/IAST

### SAST (Static Application Security Testing)

- **O que é**: Teste estático de caixa branca. Analisa o código-fonte (ou binários) sem executar a aplicação.
- **Momento de uso**: No início do desenvolvimento, integrado ao IDE ou ao processo de Pull Request / Code Review.
- **Vantagens**:
  - Aponta a linha exata do código vulnerável
  - Permite corrigir falhas antes do build
- **Desvantagens**:
  - Gera mais falsos positivos
  - Não testa o comportamento da aplicação em tempo de execução ou configurações de ambiente
- **Exemplos de ferramentas**: SonarQube, Snyk Code, GitHub Advanced Security (CodeQL)

### DAST (Dynamic Application Security Testing)

- **O que é**: Teste dinâmico de caixa preta. Simula ataques externos em uma aplicação em execução (em homologação, staging ou produção).
- **Momento de uso**: Nas fases finais do ciclo, logo antes do lançamento ou em ambientes de teste.
- **Vantagens**:
  - Não precisa do código-fonte
  - Valida falhas reais que podem ser exploradas por atacantes
  - Agnóstico à linguagem de programação
- **Desvantagens**:
  - Não diz em qual linha exata do código está o erro
  - Exige uma aplicação funcional rodando para ser testada
- **Exemplos de ferramentas**: Ferramentas de varredura automatizada de vulnerabilidades web (simulando OWASP Top 10)

### IAST (Interactive Application Security Testing)

- **O que é**: Análise interativa que combina o melhor do SAST e do DAST. Utiliza um agente instalado no servidor (ou dentro do runtime da aplicação) para monitorar o código, o fluxo de dados e as requisições em tempo real.
- **Momento de uso**: Durante os testes funcionais ou de integração, enquanto a aplicação é executada.
- **Vantagens**:
  - Alta precisão
  - Baixo índice de falsos positivos
  - Capacidade de apontar exatamente onde a vulnerabilidade acontece no fluxo da aplicação
- **Desvantagens**:
  - Pode gerar leve impacto no desempenho do aplicativo por rodar embutido no ambiente de execução
- **Exemplos de ferramentas**: Contrast Security

### Como elas se complementam na esteira DevSecOps

- **SAST** age cedo (Shift-Left) limpando erros de sintaxe, más práticas e falhas lógicas no código.
- **IAST** monitora o comportamento interno enquanto a aplicação é testada pelos desenvolvedores ou QA.
- **DAST** valida a aplicação "de fora para dentro", testando o que realmente está exposto no ambiente final.
- **Dica de integração**: Os dados e achados do DAST podem refinar as regras do SAST, criando um ciclo contínuo de amadurecimento da segurança.
