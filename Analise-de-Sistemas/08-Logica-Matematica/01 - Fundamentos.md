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

Um **argumento** é um conjunto de proposições em que algumas, chamadas **premissas**, são apresentadas como razões para aceitar outra, chamada **conclusão**. A validade do argumento depende da relação lógica entre as premissas e a conclusão, não do assunto tratado nem de as premissas serem de fato verdadeiras.

### Estrutura e representação

As premissas são normalmente indicadas antes da conclusão, que pode ser precedida por expressões como “portanto”, “logo” ou “consequentemente”. Se $P_1, P_2, \ldots, P_n$ são as premissas e $C$ é a conclusão, o argumento pode ser representado assim:

$$
P_1,\ P_2,\ \ldots,\ P_n\ \therefore C
$$

O símbolo $\therefore$ significa “portanto”. Por exemplo:

1. Se um número é divisível por 4, então é par.
2. 12 é divisível por 4.
3. Portanto, 12 é par.

Nesse argumento, as duas primeiras proposições são premissas e a última é a conclusão.

### Validade e invalidade

Um argumento é **válido** quando não existe uma situação em que todas as premissas sejam verdadeiras e a conclusão seja falsa. Em outras palavras, se as premissas forem verdadeiras, a conclusão necessariamente também será verdadeira.

Para verificar a validade usando conectivos, forma-se a condicional cujo antecedente é a conjunção das premissas e cujo consequente é a conclusão:

$$
(P_1 \land P_2 \land \cdots \land P_n) \rightarrow C
$$

O argumento é válido quando essa fórmula é uma **tautologia**, isto é, verdadeira em todas as valorações. É **inválido** quando há ao menos uma valoração que torna todas as premissas verdadeiras e a conclusão falsa; essa valoração é um **contraexemplo** ao argumento.

Exemplo de argumento inválido:

1. Se estudo, então sou aprovado.
2. Sou aprovado.
3. Portanto, estudei.

É possível que a conclusão seja falsa e as premissas verdadeiras? Se alguém for aprovado por outro motivo, sim: a primeira premissa pode ser verdadeira e a segunda também, embora a pessoa não tenha estudado. Logo, o argumento não é válido. A forma inválida é chamada **afirmação do consequente**.

### Verdade das premissas e solidez

**Validade** não é o mesmo que **verdade**: a validade avalia a forma do raciocínio; a verdade avalia cada proposição. Um argumento pode ser válido mesmo que uma ou mais premissas sejam falsas.

Um argumento é **sólido** quando é válido e, além disso, todas as suas premissas são verdadeiras. Nesse caso, a conclusão também é verdadeira. Um argumento inválido não se torna válido apenas por acaso ter uma conclusão verdadeira.

### Formas válidas de inferência

Algumas formas recorrentes de argumentos válidos são:

#### Modus ponens

$$
P \rightarrow Q,\quad P\quad \therefore Q
$$

Se $P$ implica $Q$ e $P$ ocorre, conclui-se $Q$.

#### Modus tollens

$$
P \rightarrow Q,\quad \neg Q\quad \therefore \neg P
$$

Se $P$ implica $Q$ e $Q$ não ocorre, conclui-se que $P$ não ocorreu.

#### Silogismo disjuntivo

$$
P \lor Q,\quad \neg P\quad \therefore Q
$$

Se pelo menos uma entre $P$ e $Q$ é verdadeira e $P$ é falsa, conclui-se $Q$.

#### Silogismo hipotético

$$
P \rightarrow Q,\quad Q \rightarrow R\quad \therefore P \rightarrow R
$$

Se $P$ implica $Q$ e $Q$ implica $R$, então $P$ implica $R$. A conclusão encadeia as duas condicionais.

Reconhecer a forma lógica ajuda a distinguir uma conclusão que decorre necessariamente das premissas de uma conclusão que apenas parece plausível.

## 3. A lógica sentencial

A **lógica sentencial**, também chamada de **lógica proposicional**, estuda como o valor de verdade de proposições compostas depende dos valores de verdade de suas partes e dos conectivos que as relacionam. Ela considera cada proposição simples como uma unidade, sem analisar sua estrutura interna.

### Proposições simples e compostas

Uma **proposição simples** (ou atômica) não contém outra proposição como componente lógico. Por convenção, letras como $P$, $Q$ e $R$ representam proposições simples. Por exemplo:

- $P$: “Está chovendo.”
- $Q$: “A rua está molhada.”

Uma **proposição composta** é formada pela combinação de proposições simples por meio de conectivos. Com as proposições anteriores:

- $\neg P$: “Não está chovendo.”
- $P \land Q$: “Está chovendo e a rua está molhada.”
- $P \rightarrow Q$: “Se está chovendo, então a rua está molhada.”

Na lógica sentencial, interessa a forma lógica dessas expressões. A análise não verifica, por si só, se está realmente chovendo ou se a rua está molhada.

### Simbolização

Simbolizar consiste em substituir proposições simples por letras e representar os conectivos de modo explícito. Isso permite analisar a estrutura do raciocínio sem depender do conteúdo em linguagem natural.

Por exemplo, sejam:

- $P$: “O sistema está disponível.”
- $Q$: “Os usuários conseguem acessar o serviço.”

A frase “O sistema está disponível e os usuários conseguem acessar o serviço” é simbolizada por $P \land Q$. Já “Se o sistema está disponível, então os usuários conseguem acessar o serviço” é simbolizada por $P \rightarrow Q$.

A simbolização deve preservar a relação expressa pela frase. Em particular, “ou” costuma ser representado pela disjunção inclusiva ($\lor$): basta que ao menos uma das proposições seja verdadeira, podendo ambas também ser verdadeiras.

### Fórmulas e escopo

As letras proposicionais e os conectivos formam **fórmulas**. Parênteses indicam como a fórmula deve ser agrupada e qual é o alcance de cada conectivo. Por exemplo, $P \land (Q \lor R)$ afirma que $P$ se combina com a disjunção entre $Q$ e $R$; já $(P \land Q) \lor R$ combina a conjunção entre $P$ e $Q$ com $R$. Essas fórmulas podem ter valores de verdade diferentes para os mesmos valores de $P$, $Q$ e $R$.

Quando os parênteses são omitidos, uma convenção comum de precedência é: negação, conjunção, disjunção, condicional e bicondicional, nessa ordem. Ainda assim, o uso de parênteses é recomendado quando houver possibilidade de ambiguidade. As regras completas de formação de fórmulas são tratadas no tópico sobre regras de formação.

### Tautologia, contradição e contingência

Uma fórmula pode ser classificada conforme seu valor de verdade em todas as combinações possíveis de valores para suas proposições simples:

- **Tautologia:** verdadeira em todas as combinações. Exemplo: $P \lor \neg P$.
- **Contradição:** falsa em todas as combinações. Exemplo: $P \land \neg P$.
- **Contingência:** verdadeira em algumas combinações e falsa em outras. Exemplo: $P \land Q$.

As tabelas de verdade permitem verificar essas classificações. Com $n$ proposições simples distintas, é necessário considerar $2^n$ combinações possíveis de valores de verdade.

### Equivalência lógica

Duas fórmulas são **logicamente equivalentes** quando têm o mesmo valor de verdade em todas as combinações possíveis para suas proposições simples. A equivalência é indicada por $\equiv$. Por exemplo, a negação de uma conjunção equivale à disjunção das negações:

$$
\neg(P \land Q) \equiv \neg P \lor \neg Q
$$

A equivalência pode ser verificada comparando as colunas das fórmulas em uma tabela de verdade. Ela permite substituir uma fórmula por outra sem alterar o valor lógico de uma expressão maior. Algumas equivalências importantes são:

| Nome | Expressão | Equivalência |
|---|---|---|
| Dupla negação | $\neg\neg P$ | $P$ |
| Lei de De Morgan | $\neg(P \land Q)$ | $\neg P \lor \neg Q$ |
| Lei de De Morgan | $\neg(P \lor Q)$ | $\neg P \land \neg Q$ |
| Implicação material | $P \rightarrow Q$ | $\neg P \lor Q$ |
| Contraposição | $P \rightarrow Q$ | $\neg Q \rightarrow \neg P$ |
| Bicondicional | $P \leftrightarrow Q$ | $(P \rightarrow Q) \land (Q \rightarrow P)$ |
| Comutatividade da conjunção | $P \land Q$ | $Q \land P$ |
| Comutatividade da disjunção | $P \lor Q$ | $Q \lor P$ |
| Associatividade | $(P \land Q) \land R$ | $P \land (Q \land R)$ |
| Distributividade | $P \land (Q \lor R)$ | $(P \land Q) \lor (P \land R)$ |

#### Exemplos de aplicação

Seja $P$: “está chovendo” e $Q$: “a rua está molhada”. A condicional “se está chovendo, então a rua está molhada” pode ser reescrita pela implicação material como “não está chovendo ou a rua está molhada”:

$$
P \rightarrow Q \equiv \neg P \lor Q
$$

Também é possível transformar uma negação aplicando as leis de De Morgan. “Não é verdade que está chovendo e a rua está molhada” equivale a “não está chovendo ou a rua não está molhada”:

$$
\neg(P \land Q) \equiv \neg P \lor \neg Q
$$

As equivalências podem ser usadas em sequência. Por exemplo:

$$
\neg(P \rightarrow Q)
\equiv \neg(\neg P \lor Q)
\equiv P \land \neg Q
$$

Assim, a negação de “se $P$, então $Q$” só é verdadeira quando $P$ é verdadeira e $Q$ é falsa — exatamente o caso em que a condicional é falsa.

### Limites da lógica sentencial

A lógica sentencial trata cada proposição simples como indivisível. Assim, não representa diretamente a estrutura interna de frases como “todo usuário possui uma conta” ou “algum sistema está indisponível”. Para analisar objetos, propriedades e quantificadores como “todo” e “algum”, utiliza-se a lógica de predicados de primeira ordem, apresentada no tópico seguinte.

## 4. A lógica de predicados de primeira ordem
