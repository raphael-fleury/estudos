# Fundamentos da Lógica Matemática

## 1. Conectivos

No sentido lógico-matemático convencional, os conectivos são operadores usados para combinar proposições — sentenças que podem ser verdadeiras ou falsas — de maneira estritamente formal. O valor de verdade da nova frase depende **apenas** dos valores de verdade das proposições originais, sem considerar relações de causa, tempo ou contexto entre elas.

### Os cinco conectivos lógicos principais

#### 1. Negação ($\neg P$ ou $\sim P$)

- **Nome:** "não".
- **Função:** inverte o valor de verdade da proposição.
- **Regra:** se uma proposição é verdadeira, sua negação é falsa, e vice-versa.

#### 2. Conjunção ($P \land Q$)

- **Nome:** "e".
- **Função:** une duas proposições, exigindo que ambas sejam verdadeiras.
- **Regra:** só é **verdadeira se ambas as proposições forem verdadeiras**. Se pelo menos uma for falsa, o resultado é falso.

#### 3. Disjunção inclusiva ($P \lor Q$)

- **Nome:** "ou".
- **Função:** indica alternativas: uma proposição, a outra ou ambas podem ser verdadeiras.
- **Regra:** só é **falsa se ambas as proposições forem falsas**. Se pelo menos uma for verdadeira, o resultado é verdadeiro.

#### 4. Condicional ($P \rightarrow Q$ ou $P \supset Q$)

- **Nome:** "se... então".
- **Função:** expressa uma condição suficiente, do antecedente ($P$) para o consequente ($Q$).
- **Regra:** só é **falsa quando o antecedente é verdadeiro e o consequente é falso** ($V \rightarrow F$). Nos outros casos, inclusive quando o antecedente é falso, é convencionalmente verdadeira.

#### 5. Bicondicional ($P \leftrightarrow Q$)

- **Nome:** "se e somente se".
- **Função:** expressa uma equivalência mútua entre duas proposições.
- **Regra:** é **verdadeira quando ambas têm o mesmo valor de verdade** — ambas verdadeiras ou ambas falsas. Se os valores forem diferentes, é falsa.

### Tabela de verdade comparativa

A tabela mostra o comportamento dos cinco conectivos para as proposições $P$ e $Q$. A negação apresentada é a de $P$.

| $P$ | $Q$ | $\neg P$ | $P \land Q$ | $P \lor Q$ | $P \rightarrow Q$ | $P \leftrightarrow Q$ |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| V | V | F | V | V | V | V |
| V | F | F | F | V | F | F |
| F | V | V | F | V | V | F |
| F | F | V | F | F | V | V |

## 2. Argumentos
## 3. A lógica sentencial
## 4. A lógica de predicados de primeira ordem
