# Modelagem

## 1. Modelagem de dados (conceitual, lógica e física)

Modelagem de dados é o processo de representar os dados de uma organização, seus significados, relacionamentos e regras de negócio. O modelo serve como referência para análise, desenvolvimento, integração e manutenção dos bancos de dados.

### Objetivos

- Identificar quais informações precisam ser armazenadas.
- Definir o significado e o relacionamento entre os dados.
- Evitar redundância, inconsistência e ambiguidade.
- Documentar regras de negócio e apoiar a comunicação entre usuários, analistas e desenvolvedores.
- Orientar a implementação e a evolução do banco de dados.

### Níveis de modelagem

#### Modelo conceitual

É a visão de mais alto nível dos dados, independente de tecnologia e de detalhes de implementação. Representa os principais conceitos do negócio, seus atributos relevantes e os relacionamentos entre eles.

Características:

- É compreensível por usuários de negócio e equipes técnicas.
- Concentra-se no **o que** existe no domínio, e não em **como** será armazenado.
- Normalmente é representado por um diagrama entidade-relacionamento (DER).
- Não define tabelas, tipos de dados, índices ou chaves de um SGBD específico.

Exemplo: uma `Venda` é realizada por um `Cliente` e contém um ou mais `Produtos`.

#### Modelo lógico

Detalha a estrutura dos dados com base em um modelo de dados, geralmente o modelo relacional, mas ainda sem depender completamente de um SGBD específico. As entidades são transformadas em relações ou tabelas, e os relacionamentos passam a ser expressos por chaves.

Elementos comuns:

- Tabelas ou relações.
- Colunas e seus domínios de valores.
- Chaves primárias (identificam unicamente cada registro).
- Chaves estrangeiras (referenciam registros de outra tabela).
- Cardinalidades e restrições de integridade.
- Normalização para reduzir redundância e anomalias de atualização.

Exemplo:

```text
CLIENTE (id_cliente, nome, email)
VENDA (id_venda, data_venda, id_cliente)
PRODUTO (id_produto, descricao, preco)
ITEM_VENDA (id_venda, id_produto, quantidade)
```

Nesse exemplo, `id_cliente` em `VENDA` referencia `CLIENTE`, enquanto `ITEM_VENDA` resolve o relacionamento muitos-para-muitos entre `VENDA` e `PRODUTO`.

#### Modelo físico

Descreve como os dados serão efetivamente armazenados e acessados em um SGBD específico. Considera requisitos de desempenho, segurança, disponibilidade e capacidade.

Pode incluir:

- Tipos de dados específicos do SGBD.
- Definição de tabelas, constraints, índices e particionamento.
- Estratégias de armazenamento e organização dos arquivos.
- Views, gatilhos, procedures e funções.
- Políticas de acesso, criptografia e auditoria.
- Configurações de desempenho, backup e recuperação.

O modelo físico pode ser otimizado sem alterar o significado do modelo conceitual. Por exemplo, a criação de um índice sobre `VENDA.id_cliente` pode acelerar consultas, mas não muda a regra de que cada venda pertence a um cliente.

### Comparação entre os níveis

| Nível | Foco | Dependência tecnológica | Principal resultado |
| --- | --- | --- | --- |
| Conceitual | Conceitos e regras do negócio | Independente | Visão geral do domínio e DER |
| Lógico | Estrutura e relacionamentos dos dados | Baixa ou moderada | Esquema lógico com tabelas e chaves |
| Físico | Armazenamento e acesso | Alta | Implementação no SGBD |

### Transformação entre os modelos

Uma entidade conceitual normalmente origina uma tabela no modelo lógico. Seus atributos tornam-se colunas, o identificador torna-se chave primária e os relacionamentos são implementados por chaves estrangeiras ou tabelas associativas. No modelo físico, essa estrutura recebe tipos de dados, índices e demais recursos específicos do SGBD.

As transformações devem preservar as regras de negócio. Alterações no modelo físico não devem violar a estrutura lógica, e alterações no modelo lógico devem ser avaliadas quanto ao impacto no modelo conceitual e nos sistemas que utilizam os dados.
## 2. Criação e alteração dos modelos lógico e físico de dados
## 3. O modelo Relacional
## 4. Normalização das estruturas de dados
## 5. Integridade referencial
## 6. Metadados
## 7. Modelagem dimensional
## 8. Avaliação de modelos de dados
## 9. Técnicas de engenharia reversa para criação e atualização de modelos de dados
