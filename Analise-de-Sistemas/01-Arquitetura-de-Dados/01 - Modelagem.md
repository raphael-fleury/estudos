# Modelagem

Modelagem de dados é o processo de representar os dados de uma organização, seus significados, relacionamentos e regras de negócio. O modelo serve como referência para análise, desenvolvimento, integração e manutenção dos bancos de dados.
### Objetivos

- Identificar quais informações precisam ser armazenadas.
- Definir o significado e o relacionamento entre os dados.
- Evitar redundância, inconsistência e ambiguidade.
- Documentar regras de negócio e apoiar a comunicação entre usuários, analistas e desenvolvedores.
- Orientar a implementação e a evolução do banco de dados.

## 1. Níveis conceituais, lógicos e físicos

### Nível Conceitual

- **O que é:** A visão geral e abstrata dos dados do negócio.
- **Foco:** Entender quais informações são importantes para a empresa e como elas se ligam.
- **Características:**
    - Totalmente independente de tecnologia, programas ou SGBD (Sistema Gerenciador de Banco de Dados).
    - Usa o MER (Modelo Entidade-Relacionamento) com entidades, atributos principais e relacionamentos.
    - Linguagem simples para leigos e analistas conversarem.

**Exemplo:** uma `Venda` é realizada por um `Cliente` e contém um ou mais `Produtos`.
### Nível Lógico

- **O que é:** A tradução do modelo conceitual para uma estrutura de dados mais técnica.
- **Foco:** Definir os atributos, tipos lógicos, chaves primárias e chaves estrangeiras.
- **Características:**
    - Independente de um SGBD específico (como MySQL ou Oracle), mas aderente a um modelo de dados (como o relacional).
    - Detalha as tabelas, colunas e os relacionamentos de forma exata.
    - Normalização para reduzir redundância.
    - Restrições de integridade

**Exemplo:**

```text
CLIENTE (id_cliente, nome, email)
VENDA (id_venda, data_venda, id_cliente)
PRODUTO (id_produto, descricao, preco)
ITEM_VENDA (id_venda, id_produto, quantidade)
```

Nesse exemplo, `id_cliente` em `VENDA` referencia `CLIENTE`, enquanto `ITEM_VENDA` resolve o relacionamento muitos-para-muitos entre `VENDA` e `PRODUTO`.

### Nível Físico

- **O que é:** A implementação prática do banco de dados no computador.
- **Foco:** Como os dados serão gravados no disco e como otimizar a velocidade.
- **Características:**
    - Dependente de um SGBD específico (ex: PostgreSQL, SQL Server).
    - Define tipos de dados exatos (`VARCHAR`, `INT`), índices, restrições e particionamento.
    - Definição de tabelas, constraints, índices e particionamento.

### Comparação entre os níveis

| Nível      | Foco                                  | Dependência tecnológica | Principal resultado                 |
| ---------- | ------------------------------------- | ----------------------- | ----------------------------------- |
| Conceitual | Conceitos e regras do negócio         | Independente            | Visão geral do domínio e DER        |
| Lógico     | Estrutura e relacionamentos dos dados | Baixa ou moderada       | Esquema lógico com tabelas e chaves |
| Físico     | Armazenamento e acesso                | Alta                    | Implementação no SGBD               |

### Transformação entre os modelos

Uma entidade conceitual normalmente origina uma tabela no modelo lógico. Seus atributos tornam-se colunas, o identificador torna-se chave primária e os relacionamentos são implementados por chaves estrangeiras ou tabelas associativas. No modelo físico, essa estrutura recebe tipos de dados, índices e demais recursos específicos do SGBD.

As transformações devem preservar as regras de negócio. Alterações no modelo físico não devem violar a estrutura lógica, e alterações no modelo lógico devem ser avaliadas quanto ao impacto no modelo conceitual e nos sistemas que utilizam os dados.

## 2. Criação e alteração dos modelos lógico e físico de dados

A criação e a alteração dos modelos lógico e físico de dados são etapas centrais no ciclo de vida do banco de dados. Elas envolvem transformar a visão do negócio em uma estrutura coerente, acessível e eficiente, além de ajustar essa estrutura conforme o sistema evolui.

### 2.1 Criação do modelo lógico

A criação do modelo lógico parte geralmente do modelo conceitual e da análise dos requisitos do sistema. Nessa etapa, definem-se:

- entidades e atributos;
- relacionamentos entre as entidades;
- chaves primárias e estrangeiras;
- regras de negócio que devem ser representadas no esquema;
- dependências e restrições relevantes.

Em um ambiente relacional, o objetivo é organizar os dados em tabelas e estabelecer como elas se relacionam, mantendo consistência e minimizando redundâncias.

Exemplo:

```text
CLIENTE (id_cliente PK, nome, cpf, email)
PEDIDO (id_pedido PK, data_pedido, valor_total, id_cliente FK)
PRODUTO (id_produto PK, nome, preco)
ITEM_PEDIDO (id_pedido FK, id_produto FK, quantidade, valor_unitario)
```

Nesse esquema, a tabela `PEDIDO` referencia `CLIENTE`, e `ITEM_PEDIDO` representa o relacionamento entre `PEDIDO` e `PRODUTO`.

### 2.2 Alteração do modelo lógico

O modelo lógico pode precisar de alteração por diversos motivos, como:

- inclusão de novos campos ou atributos;
- mudança de regras de negócio;
- evolução do sistema;
- ajuste de cardinalidades;
- melhoria de integridade ou normalização;
- correção de erros na modelagem inicial.

Essas alterações devem ser avaliadas com cuidado, porque qualquer mudança no esquema pode impactar consultas, processos, regras de negócio e integrações com outros sistemas.

Alguns impactos comuns são:

- alteração de campos obrigatórios ou opcionais;
- mudança de chaves ou tipos de relacionamento;
- criação de novas tabelas ou exclusão de existentes;
- alteração na normalização de dados;
- necessidade de migração dos dados já armazenados.

### 2.3 Criação do modelo físico

O modelo físico transforma o esquema lógico em uma implementação específica para um SGBD, como MySQL, PostgreSQL, SQL Server ou Oracle. Nesta etapa, considera-se a infraestrutura disponível, o volume de dados, a carga de operações e os requisitos de desempenho.

Entre os elementos normalmente definidos no modelo físico estão:

- tipos de dados dos campos;
- restrições e regras de validação;
- índices;
- chaves compostas;
- partições e segmentação;
- views;
- triggers;
- procedures;
- política de armazenamento e backup.

Exemplo físico em SQL:

```sql
CREATE TABLE CLIENTE (
    id_cliente INT PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    cpf CHAR(11) NOT NULL UNIQUE,
    email VARCHAR(150)
);

CREATE TABLE PEDIDO (
    id_pedido INT PRIMARY KEY,
    data_pedido DATE NOT NULL,
    valor_total DECIMAL(10,2) NOT NULL,
    id_cliente INT NOT NULL,
    CONSTRAINT fk_pedido_cliente FOREIGN KEY (id_cliente) REFERENCES CLIENTE(id_cliente)
);
```

### 2.4 Alteração do modelo físico

A alteração do modelo físico geralmente é feita para otimizar desempenho, corrigir limites de armazenamento, melhorar a segurança ou adaptar o banco à infraestrutura atual. Algumas mudanças comuns incluem:

- criação de índices para acelerar consultas;
- alteração de tipos de dados por mudança de escala ou precisão;
- particionamento de tabelas grandes;
- reorganização do armazenamento para reduzir custos ou melhorar I/O;
- ajustes em constraints para refletir regras operacionais;
- criação de gatilhos para automatizar validações ou auditoria.

A principal atenção é que mudanças físicas não devem, em regra, alterar a semântica do modelo lógico. O objetivo é melhorar a execução, não alterar o sentido dos dados.

### 2.5 Relação entre criação e alteração dos modelos

A criação e a alteração dos modelos lógico e físico são processos contínuos. O modelo lógico representa a estrutura correta do dado; o modelo físico representa a forma como essa estrutura será executada no banco. 

Quando novos requisitos surgem, o ciclo normalmente é:

1. analisar a necessidade do negócio;
2. atualizar o modelo conceitual e lógico;
3. verificar impactos nas regras e relacionamentos;
4. ajustar o modelo físico conforme o SGBD;
5. migrar ou converter os dados, se necessário;
6. testar desempenho, consistência e compatibilidade.

### 2.6 Considerações importantes

- O modelo lógico deve priorizar a integridade e a clareza.
- O modelo físico deve priorizar eficiência, escalabilidade e confiabilidade.
- Alterações inadequadas podem causar perda de dados, inconsistência ou queda de desempenho.
- Toda evolução do banco deve ser documentada e acompanhada de migração de dados e testes.

### 2.7 Exemplo de alteração de modelo

Suponha que uma empresa decida registrar a data da entrega de cada pedido. No modelo lógico, seria necessário incluir o atributo `data_entrega` na tabela `PEDIDO`. No modelo físico, isso significaria alterar a estrutura da tabela e provavelmente criar índices por data, caso as consultas por período sejam frequentes.

```sql
ALTER TABLE PEDIDO
ADD data_entrega DATE;

CREATE INDEX idx_pedido_data_entrega ON PEDIDO(data_entrega);
```

Essa alteração é simples do ponto de vista funcional, mas exige análise do impacto em relatórios, consultas e manutenção dos dados.

## 3. O modelo Relacional
## 4. Normalização das estruturas de dados
## 5. Integridade referencial
## 6. Metadados
## 7. Modelagem dimensional
## 8. Avaliação de modelos de dados
## 9. Técnicas de engenharia reversa para criação e atualização de modelos de dados
