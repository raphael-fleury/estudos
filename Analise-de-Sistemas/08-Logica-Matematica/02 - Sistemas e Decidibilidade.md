# Sistemas e Decidibilidade

## 1. Sistemas dedutivos

Um **sistema dedutivo** é um conjunto organizado de regras para obter conclusões a partir de premissas. Pense nele como um jogo: há regras permitidas e, seguindo essas regras, podemos demonstrar que uma conclusão decorre das hipóteses.

Um sistema costuma ter:

- **Axiomas:** fórmulas aceitas como ponto de partida, sem demonstração dentro do próprio sistema.
- **Regras de inferência:** instruções que permitem passar de fórmulas já conhecidas para outra fórmula.
- **Demonstração:** uma sequência de passos em que cada fórmula é um axioma, uma premissa ou o resultado de uma regra aplicada corretamente.

### Exemplo: modus ponens

Uma regra muito comum é o **modus ponens**:

1. Se $P$, então $Q$ ($P \rightarrow Q$).
2. $P$ é verdadeiro.
3. Portanto, $Q$.

Por exemplo: “Se o alarme está ativado, ele toca quando a porta abre. O alarme está ativado. Portanto, ele toca quando a porta abre.”

Em símbolos, escrevemos:

$$
P \rightarrow Q,\ P\ \vdash Q
$$

O símbolo $\vdash$ (“deduz”) indica que a conclusão pode ser demonstrada pelas regras do sistema a partir das premissas. Ele descreve uma **prova**, isto é, o caminho formal usado para chegar à conclusão.

### Correção e completude

Um bom sistema dedutivo deve se relacionar adequadamente com o significado das fórmulas:

- **Correção (ou solidez):** se uma conclusão pode ser demonstrada, ela realmente decorre logicamente das premissas. O sistema não permite provar conclusões inválidas.
- **Completude:** se uma conclusão realmente decorre logicamente das premissas, existe uma demonstração dela no sistema. O sistema consegue provar tudo o que é logicamente válido.

Em resumo: correção significa “não prova demais”; completude significa “não deixa de provar o que deveria”.

## 2. Decidibilidade da lógica sentencial

Um problema é **decidível** quando existe um procedimento que sempre termina e responde corretamente “sim” ou “não” para qualquer entrada válida.

Na **lógica sentencial** (ou proposicional), podemos decidir se uma fórmula é:

- **Tautologia:** verdadeira em todas as combinações possíveis de valores das proposições.
- **Contradição:** falsa em todas as combinações.
- **Contingência:** verdadeira em algumas combinações e falsa em outras.

### Como decidir usando uma tabela-verdade

1. Identifique as proposições simples diferentes na fórmula.
2. Liste todas as combinações de verdadeiro (V) e falso (F).
3. Calcule o valor da fórmula em cada linha, respeitando os conectivos.
4. Observe a coluna final: só V significa tautologia; só F significa contradição; uma mistura significa contingência.

Com $n$ proposições simples, há $2^n$ combinações. Por exemplo, com $P$ e $Q$, há $2^2 = 4$ combinações. Como esse número é finito, a tabela-verdade sempre termina. Assim, a validade de fórmulas da lógica sentencial é decidível por esse método, embora tabelas muito grandes possam dar trabalho.

Uma fórmula é **satisfatível** quando existe pelo menos uma combinação que a torna verdadeira. Portanto:

- Uma tautologia é sempre satisfatível.
- Uma contradição não é satisfatível.
- Para verificar se uma fórmula é uma tautologia, basta procurar uma linha falsa: se existir, ela não é tautologia; se não existir, é.

Também podemos usar tabelas-verdade para avaliar argumentos. Um argumento é válido quando não há uma linha em que todas as premissas sejam verdadeiras e a conclusão seja falsa. Se existir uma linha assim, ela é um **contraexemplo**.

## 3. Funções de avaliação

Uma **função de avaliação** atribui um valor de verdade a cada proposição simples e, a partir disso, calcula o valor de fórmulas maiores. Os valores normalmente usados são $V$ (verdadeiro) e $F$ (falso).

Por exemplo, considere a fórmula:

$$
(P \land Q) \rightarrow P
$$

Uma avaliação escolhe valores para $P$ e $Q$. Se $P = V$ e $Q = F$, então $P \land Q = F$; como uma condicional com antecedente falso é verdadeira, o resultado é $V$.

O cálculo é feito de dentro para fora, seguindo as regras dos conectivos:

- $\neg P$ inverte o valor de $P$.
- $P \land Q$ é verdadeiro somente quando os dois valores são verdadeiros.
- $P \lor Q$ é falso somente quando os dois valores são falsos.
- $P \rightarrow Q$ é falso somente quando $P$ é verdadeiro e $Q$ é falso.
- $P \leftrightarrow Q$ é verdadeiro quando $P$ e $Q$ têm o mesmo valor.

Para a fórmula do exemplo, a tabela completa é:

| $P$ | $Q$ | $P \land Q$ | $(P \land Q) \rightarrow P$ |
|:---:|:---:|:---:|:---:|
| V | V | V | V |
| V | F | F | V |
| F | V | F | V |
| F | F | F | V |

Como a última coluna tem apenas valores verdadeiros, a fórmula é uma tautologia.

**Em poucas palavras:** a função de avaliação diz como uma fórmula se comporta diante de uma escolha de valores para suas proposições; a tabela-verdade reúne todas as escolhas possíveis. Isso permite verificar tautologias, contradições, satisfatibilidade e validade de argumentos.
