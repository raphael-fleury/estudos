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

O modelo relacional é uma forma de organizar e gerenciar dados em um banco de dados relacional utilizando tabelas bidimensionais compostas por linhas e colunas, baseado na teoria dos conjuntos e na lógica de predicados.

### Conceitos Principais

- **Relação:** Uma tabela bidimensional que armazena os dados.
- **Tupla:** Uma linha ou registro da tabela, representando uma ocorrência ou entidade específica.
- **Atributo:** Uma coluna ou campo da tabela, representando uma característica da entidade.
- **Domínio:** O conjunto de valores permitidos para um atributo (o tipo de dado)

### Chaves e Restrições de Integridade

- **Chave Primária (Primary Key):** Um atributo ou conjunto de atributos que identifica de forma única cada tupla em uma relação.
- **Chave Estrangeira (Foreign Key):** Um atributo que faz referência à chave primária de outra tabela, garantindo a integridade referencial e conectando as informações.
- **Atomicidade:** Cada valor em uma linha deve ser indivisível (valores atômicos).

### Vantagens

- **Integridade dos Dados:** Regras rígidas evitam dados órfãos ou duplicados.
- **Conformidade ACID:** Garante atomicidade, consistência, isolamento e durabilidade nas transações.
- **Linguagem Padrão:** Utiliza o SQL para consultas e manipulação eficiente.

## 4. Normalização das estruturas de dados

A normalização de dados é um processo usado em bancos de dados relacionais para organizar tabelas, reduzir a duplicação de informações e evitar erros ao alterar, apagar ou inserir dados.

### Conceitos

#### Dependência Funcional

É um relacionamento entre dois ou mais atributos, de forma que o valor de um atributo identifica o valor do outro atributo. 

**Exemplo:** se nós sabemos qual o CPF de uma pessoa também vamos descobrir o nome. Nem sempre o inverso se aplica, como neste caso.

#### Dependência Funcional Parcial

Ocorre quando um atributo que não faz parte da chave primária depende apenas de uma parte de uma chave primária composta (formada por mais de uma coluna), e não dela inteira.

**Exemplo:** Em uma tabela de notas de alunos com a chave primária composta por `(ID_Aluno, Cod_Disciplina)`, o atributo `Nome_Aluno` depende de `ID_Aluno`, mas não de `Cod_Disciplina`.

#### Dependência Funcional Transitiva

Ocorre quando um ou mais campos de uma entidade não são dependentes diretamente da chave primária, ou de parte dela, mas sim dependente de outro campo da tabela.

**Exemplo:** Na tabela Funcionario há os campos `ID_Funcionario`, `ID_Cargo` e `Nome_Cargo`. A coluna `Nome_Cargo` depende somente da coluna `ID_Cargo` que não é a coluna primária.

#### Atributos Multivalorados

São atributos que podem conter mais de um valor para um mesmo registro. 

**Exemplo:** A entidade `Empregado` com o atributo `Telefone` (pode ter 1, 2 ou nenhum).

#### Atributos Compostos

É aquele que pode ser subdividido em partes menores (atributos simples ou atômicos), formados por uma junção de subpropriedades.

**Exemplo:** O campo `Endereco` pode ser dividido em `Logradouro`, `Numero`, `Complemento`, etc.

## 5. Integridade referencial

A integridade referencial é uma regra de banco de dados que garante que as ligações entre tabelas permaneçam exatas e consistentes.

### Como funciona

- **Chaves Estrangeiras (Foreign Key):** É imposta quando uma coluna em uma tabela aponta para a chave primária de outra tabela.
- **Validade do vínculo:** O banco de dados exige que qualquer valor inserido na chave estrangeira exista de fato na tabela de origem (ou seja nulo, se permitido).
- **Evita registros órfãos:** Impede que uma tabela tenha dados vinculados a algo que não existe (por exemplo, um pedido associado a um cliente que foi deletado ou nunca existiu).

### Ações em atualizações e exclusões

Quando você tenta apagar ou alterar um registro "pai" que está sendo referenciado, o banco pode usar regras como:
- `RESTRICT / NO ACTION`: Bloqueia a exclusão ou alteração se houver registros dependentes.
- `CASCADE`: Apaga ou atualiza automaticamente todos os registros filhos vinculados.
- `SET NULL`: Define o valor da chave estrangeira na tabela filha como NULL

## 6. Metadados

Metadados são dados que descrevem outros dados, ou seja, informações que explicam a estrutura, a organização e as características dos objetos armazenados em um sistema.


Em um banco de dados, eles incluem:

- **Estrutura das tabelas:** Nome das tabelas, nomes das colunas e a ordem em que aparecem.
- **Tipos de dados:** Se uma coluna armazena texto (`VARCHAR`), números inteiros (`INT`), datas ou booleanos.
- **Restrições (Constraints):** Chaves primárias (*Primary Keys*), chaves estrangeiras (*Foreign Keys*), regras de unicidade e campos obrigatórios (`NOT NULL`).
- **Índices e visões:** Onde os índices estão localizados e como as consultas são otimizadas.
- **Informações administrativas:** Data de criação, dono do objeto, permissões de acesso e espaço em disco ocupado

## 7. Modelagem dimensional

A modelagem dimensional é uma técnica de design de bases de dados utilizada principalmente em sistemas de Data Warehouse (DW) e Business Intelligence (BI). O seu principal objetivo é estruturar os dados de forma a otimizar a velocidade das consultas e facilitar a compreensão por parte dos utilizadores de negócio.

Ao contrário da modelagem relacional tradicional (usada em sistemas OLTP para evitar a redundância de dados), a modelagem dimensional aceita a redundância (desnormalização) para maximizar a performance de leitura.

### Estrutura base

<img src="https://hermes.dio.me/articles/cover/6690eb40-5ec6-45a8-b657-da9c41b3ce7e.png" />

#### Tabelas fato (Fact Tables)

Contêm as métricas quantitativas ou medidas numéricas de um evento de negócio.

- **O que armazena:** Valores que podem ser somados, calculados ou medidos (ex: quantidade vendida, valor de faturação, tempo de espera).
- **Chaves:** Contém chaves estrangeiras (FK) que se ligam às tabelas de dimensão.
- **Características:** Cresce muito rapidamente em volume (milhões de linhas).


#### Tabelas de Dimensão (Dimension Tables)

Contêm o contexto que envolve o evento de negócio. Respondem às perguntas de "Quem?, O quê?, Onde?, Quando?, Porquê?".
- **O que armazena:** Atributos textuais e descritivos (ex: nome do cliente, categoria do produto, cidade da loja, data).
- **Chaves:** Contém uma chave primária (geralmente uma Surrogate Key ou chave artificial) que se liga à tabela de factos.
- **Características:** São tabelas mais largas (muitas colunas) e com menos linhas que as tabelas de factos.


### Modelos de Arquitetura Mais Comuns

#### Esquema em Estrela (Star Schema)

É o modelo mais simples e utilizado. A tabela de factos fica no centro, rodeada diretamente pelas tabelas de dimensão.
- **Vantagem:** Consultas muito rápidas (poucos JOINs) e estrutura fácil de entender.
- **Desvantagem:** As dimensões são totalmente desnormalizadas, gerando duplicidade de dados textuais.

#### Esquema em Floco de Neve (Snowflake Schema)

É uma variação do Star Schema, onde as tabelas de dimensão são normalizadas (divididas em sub-tabelas).
- **Vantagem:** Reduz a redundância e economiza espaço em disco.
- **Desvantagem:** Consultas mais lentas e complexas devido ao maior número de JOINs.

<img src="https://media.licdn.com/dms/image/v2/D4D22AQGPX3aR01uP3w/feedshare-shrink_800/B4DZoevdalIkAg-/0/1761452361168?e=2147483647&v=beta&t=lM6rvQeKn5acRol9M-nmhhTHrm53fdFEDpTppJcFg5E"/>

## 8. Avaliação de modelos de dados

Avaliar um modelo de dados é verificar se ele representa corretamente as necessidades do negócio e se pode ser implementado e mantido com qualidade. A avaliação deve considerar os modelos conceitual, lógico e físico, pois cada nível tem objetivos e critérios próprios.

### Critérios de avaliação

- **Aderência aos requisitos:** entidades, atributos, relacionamentos e regras de negócio relevantes estão representados, sem informações importantes ausentes ou ambíguas.
- **Correção semântica:** nomes e definições refletem o significado dos dados; cardinalidades e obrigatoriedades correspondem às regras do domínio.
- **Integridade e consistência:** chaves, restrições e regras impedem registros inválidos, órfãos ou contraditórios.
- **Redundância e normalização:** os dados estão organizados para reduzir duplicidade e anomalias de inserção, atualização e exclusão. Desnormalizações devem ser justificadas por requisitos de consulta ou desempenho.
- **Desempenho:** o modelo físico atende aos padrões esperados de leitura e escrita, considerando consultas, índices, volume e concorrência.
- **Escalabilidade e flexibilidade:** a estrutura suporta crescimento e mudanças previsíveis sem exigir alterações desproporcionais ou arriscadas.
- **Segurança e privacidade:** dados sensíveis são identificáveis e podem receber controles de acesso, retenção e proteção compatíveis com sua classificação.
- **Manutenibilidade e compreensão:** o esquema é documentado, consistente e compreensível por quem precisa desenvolvê-lo, operá-lo ou evoluí-lo.

### Como avaliar

1. **Validar com os requisitos e as regras de negócio:** conferir se cada requisito de dados está representado e se as regras podem ser expressas no modelo.
2. **Revisar o diagrama e o dicionário de dados:** verificar nomes, definições, chaves, cardinalidades, opcionalidade e consistência de convenções.
3. **Analisar a normalização:** examinar dependências funcionais e formas normais para identificar redundâncias e anomalias; avaliar separadamente qualquer desnormalização.
4. **Percorrer cenários de uso:** simular operações e consultas representativas, verificando se o modelo permite realizá-las sem contornar as regras de integridade.
5. **Prototipar e testar o modelo físico:** criar o esquema em ambiente controlado e medir consultas e operações com dados e volumes representativos. Ajustes de índices e particionamento devem ser baseados em evidências.
6. **Avaliar impactos de mudanças:** verificar efeitos sobre dados existentes, aplicações, integrações, relatórios e migrações antes de aprovar alterações.

### Indicadores e trade-offs

Podem ser observados indicadores como cobertura dos requisitos, quantidade de regras de negócio não implementadas, ocorrência de dados duplicados ou inválidos, tempo de resposta das consultas e esforço para realizar mudanças. Os limites de aceitação devem ser definidos conforme os requisitos do sistema; não há um único indicador que determine a qualidade do modelo.

Os critérios podem entrar em conflito. Por exemplo, maior normalização tende a reduzir redundância, enquanto uma desnormalização controlada pode melhorar determinadas consultas. A decisão deve registrar o motivo, os benefícios, os riscos e como o resultado será monitorado. Um modelo adequado equilibra correção, integridade, desempenho e facilidade de evolução, em vez de otimizar apenas um aspecto.

## 9. Técnicas de engenharia reversa para criação e atualização de modelos de dados

A engenharia reversa em modelagem de dados é o processo de extrair informações de uma base de dados ou script existente para reconstruir seu modelo lógico, físico ou conceitual quando a documentação original está desatualizada ou ausente.

### Fontes e técnicas

- **Engenharia reversa do esquema:** extrair do catálogo do SGBD tabelas, colunas, tipos, chaves primárias e estrangeiras, restrições, índices, visões e outros objetos. Ferramentas CASE e recursos de engenharia reversa de clientes de banco de dados podem gerar diagramas a partir desses metadados.
- **Análise de scripts e migrações:** examinar comandos DDL (`CREATE`, `ALTER`, `DROP`) e o histórico de migrações para reconstruir a evolução do esquema e identificar decisões que não aparecem no estado atual.
- **Análise de código e consultas:** localizar SQL, mapeamentos objeto-relacional, procedimentos armazenados, relatórios e integrações para entender como as estruturas são utilizadas e quais dependências existem.
- **Inspeção dos dados:** analisar amostras e estatísticas — como valores nulos, duplicidades, faixas e distribuição — para identificar padrões e possíveis inconsistências. Os dados ajudam a formular hipóteses, mas não substituem regras de negócio nem provam a semântica dos campos.
- **Reconstrução do modelo conceitual:** entrevistar usuários e responsáveis pelo sistema para esclarecer o significado das entidades, as regras de negócio e os relacionamentos que não podem ser inferidos apenas do esquema.

### Processo de trabalho

1. **Definir escopo e obter acesso autorizado:** identificar bancos, esquemas, ambientes e objetos relevantes, evitando alterações no ambiente de produção durante a coleta.
2. **Extrair e registrar os metadados:** obter a definição dos objetos e, quando necessário, as dependências entre eles. Preservar a origem e a versão das informações coletadas.
3. **Gerar um modelo inicial:** importar o esquema para uma ferramenta de modelagem ou documentá-lo em diagramas e dicionário de dados. Conferir se objetos e restrições foram representados corretamente.
4. **Complementar a semântica:** validar nomes, finalidades, cardinalidades, opcionalidade e regras com documentação, código e especialistas do domínio. Distinguir fatos observados de hipóteses ainda não confirmadas.
5. **Comparar com o modelo existente:** identificar objetos ausentes ou divergentes, mudanças não documentadas e diferenças entre ambientes ou versões.
6. **Planejar e validar a atualização:** propor alterações no modelo lógico e físico, avaliar impactos e produzir scripts de migração revisáveis. Testá-los em ambiente não produtivo, incluindo a preservação e a consistência dos dados.
7. **Sincronizar a documentação:** atualizar diagramas, dicionário de dados e histórico de mudanças junto com a implementação aprovada.

### Comparação de esquemas e controle de mudanças

Ferramentas de comparação (*schema diff*) confrontam dois esquemas — por exemplo, desenvolvimento e produção ou duas versões do modelo — e apresentam diferenças como inclusão, remoção ou alteração de tabelas, colunas, chaves e índices. O resultado deve ser revisado antes de gerar ou executar DDL: uma diferença tecnicamente válida pode causar perda de dados, incompatibilidade com aplicações ou indisponibilidade.

Para atualizações, é recomendável versionar as migrações, aplicá-las em ordem e definir procedimentos de validação e recuperação. Alterações incompatíveis podem exigir etapas intermediárias, como adicionar uma coluna, migrar os dados e só então remover a estrutura antiga. A estratégia depende do SGBD, do volume de dados e dos requisitos de disponibilidade.

### Limitações e cuidados

- A estrutura física revela restrições explícitas, mas nem sempre expressa todas as regras de negócio; algumas podem estar apenas no código ou nos processos.
- Convenções de nomes, ausência de chaves estrangeiras e dados inconsistentes podem dificultar a identificação de relacionamentos.
- O esquema atual mostra o estado presente, não necessariamente as razões das decisões anteriores; scripts e histórico de versões complementam essa visão.
- A análise de dados deve respeitar controles de acesso, privacidade e minimização: utilizar dados anonimizados ou amostras apropriadas sempre que possível.
- A engenharia reversa produz uma representação a ser validada, não uma confirmação automática de que o modelo original está correto ou completo.
