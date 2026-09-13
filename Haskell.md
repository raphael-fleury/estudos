# Características da linguagem

## Índice

- [[#Imutabilidade]]
- [[#Sintaxe Básica]]
- [[#Funções de Primeira Classe]]
- [[#Recursividade]]
- [[#Programação Imperativa vs. Declarativa]]
- [[#Lazy Evaluation (Avaliação Preguiçosa)]]
- [[#Comandos GHCi]]
- [[#Tipos Genéricos (Polimorfismo Paramétrico)]]
- [[#Compreensão de Listas]]
- [[#Principais Funções de Lista]]
- [[#Tuplas]]
- [[#Data Constructors (Tipos Algébricos)]]
- [[#Record Syntax]]
- [[#Typeclasses]]
- [[#Monóides]]
- [[#Funtores]]
- [[#Funtores Aplicativos]]
- [[#Mônadas]]

---

## Imutabilidade

Em Haskell, variáveis não mudam de valor após definidas — são como constantes matemáticas.

**Vantagens:**
- Evita efeitos colaterais
- Facilita debug e testes
- Código mais previsível
- Mais seguro para concorrência/paralelismo

```haskell
-- Isso NÃO modifica x, cria um novo valor
let x = 5
let y = x + 1  -- y = 6, x continua 5
x = x + 1 -- não é possível fazer isso
```

---

## Sintaxe Básica

https://www.youtube.com/watch?v=gK0hMxJhqwM

### Declaração de função

```haskell
-- sem assinatura de tipo
soma x y = x + y
-- nomeDaFuncao arg1 arg2 = retorno

-- com assinatura (recomendado)
soma :: Int -> Int -> Int
soma x y = x + y
```

### Assinatura de tipo

A assinatura de tipo é opcional (Haskell a infere), mas é uma boa prática — serve como documentação e captura erros mais cedo.

```haskell
--  nome  ::  tipo do arg 1  ->  tipo do arg 2  ->  tipo do retorno
    soma  ::  Int            ->  Int            ->  Int
    soma x y = x + y
```

- `::` se lê "tem tipo"
- O último tipo é sempre o retorno; todos os anteriores são argumentos

```haskell
-- Exemplos de assinaturas       -- Exemplos de chamada
impar      :: Int -> Bool        -- impar 1 = True, impar 2 = False
maiorQue   :: Int -> Int -> Bool -- 2 `maiorQue` 1 = True
extenso    :: Int -> String      -- extenso 2 = "dois"

identity   :: a -> a             -- genérico: funciona para qualquer tipo
```

### Pattern matching

Haskell testa os padrões de cima para baixo, usando o primeiro que casar:

```haskell
fatorial :: Int -> Int
fatorial 0 = 1                     -- padrão literal: casa só com 0
fatorial n = n * fatorial (n - 1)  -- padrão variável: casa com qualquer Int

-- Em listas
primeiro :: [a] -> a
primeiro (x:_) = x   -- x é o primeiro elemento, _ ignora o restante

tamanho :: [a] -> Int
tamanho []     = 0
tamanho (_:xs) = 1 + tamanho xs -- xs é o resto da lista sem o primeiro elemento

-- Em tuplas
somar :: (Int, Int) -> Int
somar (x, y) = x + y
```

### If/then/else

Sempre precisa do `else` — em Haskell, `if` é uma expressão que sempre retorna um valor:

```haskell
abs' :: Int -> Int
abs' x = if x >= 0 then x else -x

-- Pode ser aninhado (use guardas para mais legibilidade)
sinal :: Int -> String
sinal x = if x > 0 then "positivo" else if x < 0 then "negativo" else "zero"
```

### Guardas

Mais legível que `if` aninhado para múltiplas condições:

```haskell
classifica :: Int -> String
classifica n
  | n < 0     = "negativo"
  | n == 0    = "zero"
  | n < 10    = "pequeno"
  | otherwise = "grande"   -- otherwise = True, sempre casa
```

### `where` — definições locais

`where` define auxiliares no final da função, visíveis apenas nela:

```haskell
bmi :: Double -> String
bmi peso
  | indice < 18.5 = "abaixo do peso"
  | indice < 25.0 = "normal"
  | indice < 30.0 = "acima do peso"
  | otherwise     = "obesidade"
  where
    indice = peso / altura ^ 2
    altura = 1.75             -- constante local

-- where pode definir funções também
circunferencia :: Double -> Double
circunferencia r = duasPi * r
  where duasPi = 2 * pi
```

### `let` — expressões locais

`let` é uma expressão (retorna um valor); `where` é uma declaração (fica no final):

```haskell
-- let ... in ...
area :: Double -> Double -> Double
area base altura =
  let metade = base / 2
      h      = altura
  in metade * h

-- No GHCi, let sem in define uma variável na sessão:
let x = 42
let dobro n = n * 2
```

### Aplicação parcial (currying)

Chamar uma função com menos argumentos do que ela precisa retorna uma nova função:

```haskell
soma :: Int -> Int -> Int
soma x y = x + y

soma5 :: Int -> Int
soma5 = soma 5      -- fixa o primeiro argumento

soma5 3   -- 8
soma5 10  -- 15

-- Muito útil com map, filter, etc.:
map (soma 10) [1,2,3]     -- [11,12,13]
filter (> 3) [1,2,3,4,5]  -- [4,5]
```

### Seções de operadores

Operadores podem ser parcialmente aplicados entre parênteses:

```haskell
(+3)       -- função que soma 3
(*2)       -- função que dobra
(>0)       -- função que testa se positivo
(`div` 2)  -- divide por 2

map (+3) [1,2,3]        -- [4,5,6]
filter (>0) [-1,0,1,2]  -- [1,2]
```

### Operador `$` — aplicação com precedência mínima

`$` aplica a função à esquerda ao argumento da direita, evitando parênteses:

```haskell
-- Sem $:
print (map (*2) (filter even [1..10]))

-- Com $:
print $ map (*2) $ filter even [1..10]

-- f $ x  =  f x, mas $ tem precedência mais baixa que aplicação normal
sum $ map (^2) [1..5]   -- 55  (equivale a sum (map (^2) [1..5]))
```

### Composição de funções

O operador `.` compõe funções da direita para a esquerda:

```haskell
-- (f . g) x  =  f (g x)
negativo :: Int -> Bool
negativo = not . (> 0)   -- primeiro aplica (> 0), depois not

negativo 5    -- False
negativo (-3) -- True

-- Encadeando várias funções:
processar :: [Int] -> [Int]
processar = map (*2) . filter even . take 10

processar [1..20]  -- [2,4,6,8,10,12,14,16,18,20]
```

---

## Recursividade

Em Haskell não existem loops (`for`, `while`) — a repetição é feita por **recursão**: uma função que chama a si mesma com um argumento menor, até atingir um **caso base** que encerra a chamada.

### Anatomia de uma função recursiva

```haskell
fatorial :: Int -> Int
fatorial 0 = 1                  -- caso base, para quando cai aqui
fatorial n = n * fatorial (n-1) -- caso recursivo, chama a si mesma com n-1
```

### Exemplos fundamentais

```haskell
-- Soma de todos os elementos de uma lista
somaLista :: [Int] -> Int
somaLista []     = 0                 -- caso base: lista vazia
somaLista (x:xs) = x + somaLista xs  -- x é a cabeça, xs é o resto

somaLista [1,2,3,4]  -- 10

-- Comprimento de uma lista
comprimento :: [a] -> Int
comprimento []     = 0
comprimento (_:xs) = 1 + comprimento xs

comprimento [5,6,7]  -- 3

-- Reverter uma lista
reverter :: [a] -> [a]
reverter []     = []
reverter (x:xs) = reverter xs ++ [x]

reverter [1,2,3]  -- [3,2,1]
```

comprimento [1,2,3,4,5] = 1 + comprimento [2,3,4,5]
comprimento [2,3,4,5] = 1 +  comprimento [3,4,5]
comprimento [3,4,5] = 1 + comprimento [4,5]
comprimento [4,5] = 1 + comprimento [5]
comprimento [5] = 1 + comprimento []
comprimento [] = 0
### Recursão mútua

Duas funções podem se chamar mutuamente:

```haskell
ehPar :: Int -> Bool
ehPar 0 = True
ehPar n = ehImpar (n - 1)

ehImpar :: Int -> Bool
ehImpar 0 = False
ehImpar n = ehPar (n - 1)

ehPar 4    -- True
ehImpar 3  -- True
```

---
## Funções de Primeira Classe

Funções podem ser tratadas como valores — atribuídas a variáveis, passadas como argumento, ou retornadas por outras funções.

```haskell
-- Função atribuída a uma variável
dobrar = (*2)

-- Passada como argumento
map dobrar [1,2,3]  -- [2,4,6]

-- Retornada por outra função (função que cria funções)
multiplicador n = (*n)
triplica = multiplicador 3
triplica 5  -- 15
```

---
## Programação Imperativa vs. Declarativa

| | Imperativa | Declarativa |
|---|---|---|
| **Foco** | *Como* fazer | *O que* fazer |
| **Estado** | Mutável | Imutável |
| **Controle** | Explícito (loops, if) | Implícito (funções, recursão) |
| **Exemplos** | Python, C, Java | Haskell, SQL, Prolog |

### Exemplo: somar os quadrados dos números pares de 1 a 10

**Python (imperativo):**
```python
resultado = 0
for i in range(1, 11):
    if i % 2 == 0:
        resultado += i * i
print(resultado)  # 220
```

**Haskell (declarativo):**
```haskell
sum [x^2 | x <- [1..10], even x]  -- 220
```

### Exemplo: retirar ímpares e dobrar os pares

**Python (imperativo):**
```python
numeros = [1, 2, 3, 4, 5, 6]
resultado = []
for n in numeros:
    if n % 2 == 0:
        resultado.append(n * 2)
# [4, 8, 12]
```

**Haskell (declarativo):**
```haskell
map (*2) (filter even [1, 2, 3, 4, 5, 6])  -- [4,8,12]
```

---

## Lazy Evaluation (Avaliação Preguiçosa)

Haskell só computa um valor quando ele é realmente necessário. Isso permite trabalhar com estruturas potencialmente infinitas.

### Demonstração no GHCi

**1. Lista infinita — só avalia o que você pede:**
```haskell
-- [1..] é uma lista infinita de inteiros
take 5 [1..]        -- [1,2,3,4,5]
take 10 [1,3..]     -- [1,3,5,7,9,11,13,15,17,19]
```

**2. `repeat` e `cycle` — sequências infinitas:**
```haskell
take 5 (repeat 42)       -- [42,42,42,42,42]
take 7 (cycle [1,2,3])   -- [1,2,3,1,2,3,1]
```

**3. `iterate` — aplicação repetida de uma função:**
```haskell
-- iterate f x = [x, f x, f(f x), ...]
take 6 (iterate (*2) 1)  -- [1,2,4,8,16,32]
take 5 (iterate (+3) 0)  -- [0,3,6,9,12]
```

**4. Fibonacci infinito (clássico de lazy evaluation):**
```haskell
fibs = 0 : 1 : zipWith (+) fibs (tail fibs)
take 10 fibs  -- [0,1,1,2,3,5,8,13,21,34]
```

**5. `takeWhile` com lista infinita:**
```haskell
-- Pega quadrados enquanto forem menores que 100
takeWhile (<100) [x^2 | x <- [1..]]  -- [1,4,9,16,25,36,49,64,81]
```

> 💡 **Por que isso funciona?** Haskell não tenta avaliar a lista infinita inteira — ele só computa os elementos à medida que `take` / `takeWhile` os solicita.

---

## Comandos GHCi

| Comando | Descrição |
|---|---|
| `:l arquivo.hs` | Carrega um arquivo |
| `:r` | Recarrega o arquivo atual |
| `:t expressão` | Mostra o tipo de uma expressão |
| `:i nome` | Informações sobre função/tipo |
| `:q` | Sai do GHCi |
| `let x = valor` | Define uma variável local |

---

## Tipos Genéricos (Polimorfismo Paramétrico)

Funções genéricas funcionam para *qualquer* tipo, representado por variáveis de tipo (`a`, `b`, etc.).

### Lendo uma assinatura de tipo

```haskell
length :: [a] -> Int
--         ^       ^
--    lista de     retorna Int
--   qualquer tipo
```

```haskell
fst    :: (a, b) -> a
snd    :: (a, b) -> b
map    :: (a -> b) -> [a] -> [b]
filter :: (a -> Bool) -> [a] -> [a]
id     :: a -> a
const  :: a -> b -> a
```

### Restrições de tipo (type classes)

Às vezes o tipo genérico precisa ter certas capacidades:

```haskell
sum     :: Num a => [a] -> a      -- a deve ser numérico
maximum :: Ord a => [a] -> a      -- a deve ser ordenável
show    :: Show a => a -> String  -- a deve ser "mostrável"
read    :: Read a => String -> a  -- a deve ser "legível"
```

### Exemplos práticos no GHCi

```haskell
:t map           -- (a -> b) -> [a] -> [b]
:t filter        -- (a -> Bool) -> [a] -> [a]
:t (++)          -- [a] -> [a] -> [a]

-- A mesma função map funciona com qualquer tipo:
map (*2) [1,2,3]          -- [2,4,6]
map length ["hi","hello"] -- [2,5]
map even [1,2,3,4]        -- [False,True,False,True]
```

### Criando funções genéricas

```haskell
swap :: (a, b) -> (b, a)
swap (x, y) = (y, x)

swap (1, "oi")   -- ("oi", 1)
swap (True, 42)  -- (42, True)
```

---

## Compreensão de Listas

```
[EXPRESSÃO | variável <- FONTE, FILTRO_1, FILTRO_2, ...]
```

```haskell
-- Quadrado de números pares até 20
[x^2 | x <- [1..20], even x]
-- [4,16,36,64,100,144,196,256,324,400]

-- Pares de (x, y) onde x+y é par
[(x,y) | x <- [1..4], y <- [1..4], even (x+y)]
-- [(1,1),(1,3),(2,2),(2,4),(3,1),(3,3),(4,2),(4,4)]
```

---

## Principais Funções de Lista

### Acesso
```haskell
head [1,2,3]   -- 1  (primeiro)
tail [1,2,3]   -- [2,3]  (sem o primeiro)
last [1,2,3]   -- 3  (último)
init [1,2,3]   -- [1,2]  (sem o último)
[1,2,3] !! 1   -- 2  (índice)
```

### Informações
```haskell
length [1,2,3]      -- 3
null []             -- True
null [1]            -- False
elem 3 [1,2,3]      -- True
notElem 4 [1,2,3]   -- True
```

### Transformação
```haskell
map (*2) [1,2,3]         -- [2,4,6]
filter even [1,2,3,4]    -- [2,4]
reverse [1,2,3]          -- [3,2,1]
concat [[1,2],[3,4]]     -- [1,2,3,4]
[1,2] ++ [3,4]           -- [1,2,3,4]
```

### Fatiamento
```haskell
take 3 [1..10]           -- [1,2,3]
drop 3 [1..10]           -- [4,5,6,7,8,9,10]
takeWhile (<5) [1..10]   -- [1,2,3,4]
dropWhile (<5) [1..10]   -- [5,6,7,8,9,10]
```

### Redução (fold)
```haskell
sum [1,2,3]       -- 6
product [1,2,3]   -- 6
maximum [3,1,2]   -- 3
minimum [3,1,2]   -- 1

-- foldl: percorre da esquerda
foldl (+) 0 [1,2,3]   -- ((0+1)+2)+3 = 6

-- foldr: percorre da direita
foldr (:) [] [1,2,3]  -- [1,2,3]  (reconstrói a lista)
```

### Combinação
```haskell
zip [1,2] ["a","b"]             -- [(1,"a"),(2,"b")]
zipWith (+) [1,2,3] [10,20,30]  -- [11,22,33]
unzip [(1,"a"),(2,"b")]         -- ([1,2],["a","b"])
```

---

## Tuplas

Estruturas que agrupam valores de tipos diferentes, com tamanho fixo.

```haskell
-- Criação
pessoa = ("João", 30, True)

-- Acesso em duplas (tuplas com 2 elementos)
fst (1, 2)   -- 1
snd (1, 2)   -- 2

-- Pattern matching em tuplas
descrever (nome, idade) = nome ++ " tem " ++ show idade ++ " anos"
descrever ("Ana", 25)   -- "Ana tem 25 anos"
```

---

## Data Constructors (Tipos Algébricos)

Haskell permite criar seus próprios tipos de dados com `data`. Cada alternativa é um **data constructor**.

### Tipo simples (enumeração)

```haskell
data Direcao = Norte | Sul | Leste | Oeste

mover :: Direcao -> String
mover Norte = "indo para o norte"
mover Sul   = "indo para o sul"
mover _     = "indo para outro lado"

mover Norte  -- "indo para o norte"
```

### Tipo com dados

Os construtores podem carregar valores:

```haskell
data Forma
  = Circulo Double
  | Retangulo Double Double
  | Triangulo Double Double Double

area :: Forma -> Double
area (Circulo r)       = pi * r ^ 2
area (Retangulo l a)   = l * a
area (Triangulo a b c) =
  let s = (a + b + c) / 2
  in sqrt (s * (s-a) * (s-b) * (s-c))

area (Circulo 5)      -- 78.53...
area (Retangulo 3 4)  -- 12.0
```

### Tipos recursivos

```haskell
data Lista a = Vazia | Cons a (Lista a)
-- Cons 1 (Cons 2 (Cons 3 Vazia))  equivale a  [1,2,3]

data Arvore a = Folha | No a (Arvore a) (Arvore a)

profundidade :: Arvore a -> Int
profundidade Folha       = 0
profundidade (No _ e d)  = 1 + max (profundidade e) (profundidade d)
```

### `deriving` — comportamentos automáticos

```haskell
data Cor = Vermelho | Verde | Azul
  deriving (Show, Eq, Ord, Enum)

show Vermelho    -- "Vermelho"
Vermelho == Azul -- False
succ Vermelho    -- Verde
[Vermelho ..]    -- [Vermelho,Verde,Azul]
```

---

## Record Syntax

Quando um construtor tem muitos campos, **record syntax** gera automaticamente funções de acesso (getters) e permite criação por nome, sem depender da ordem.

### Definição

```haskell
-- Sem record syntax
data Pessoa = Pessoa String Int String

-- Com record syntax
data Pessoa = Pessoa
  { nome  :: String
  , idade :: Int
  , email :: String
  } deriving (Show, Eq)
```

### Criação

```haskell
ana = Pessoa "Ana" 25 "ana@email.com"                          -- por posição
ana = Pessoa { nome = "Ana", email = "ana@email.com", idade = 25 }  -- por nome
```

### Acesso aos campos

```haskell
nome ana   -- "Ana"
idade ana  -- 25
email ana  -- "ana@email.com"
-- :t nome  =>  nome :: Pessoa -> String
```

### Atualização (cópia com campo modificado)

```haskell
ana2 = ana { idade = 26, email = "ana2@email.com" }

nome ana2   -- "Ana"  (preservado)
idade ana2  -- 26     (atualizado)
```

### Pattern matching com record syntax

```haskell
saudar :: Pessoa -> String
saudar Pessoa { nome = n, idade = i } =
  "Olá, " ++ n ++ "! Você tem " ++ show i ++ " anos."

saudar ana  -- "Olá, Ana! Você tem 25 anos."
```

### Combinando com múltiplos construtores

```haskell
data Animal
  = Cachorro { nomeAnimal :: String, raca   :: String }
  | Gato     { nomeAnimal :: String, indoor :: Bool   }
  deriving (Show)

rex  = Cachorro { nomeAnimal = "Rex",  raca = "Labrador" }
mimi = Gato     { nomeAnimal = "Mimi", indoor = True }

nomeAnimal rex   -- "Rex"
nomeAnimal mimi  -- "Mimi"
```

---

## Typeclasses

Typeclasses definem um **conjunto de comportamentos** que um tipo pode implementar — semelhantes a interfaces em outras linguagens, mas mais poderosas.

### Typeclasses da biblioteca padrão

| Typeclass | O que garante | Funções principais |
|---|---|---|
| `Eq` | Igualdade | `(==)`, `(/=)` |
| `Ord` | Ordenação | `(<)`, `(>)`, `compare`, `min`, `max` |
| `Show` | Conversão para String | `show` |
| `Read` | Leitura de String | `read` |
| `Num` | Operações numéricas | `(+)`, `(-)`, `(*)`, `abs`, `negate` |
| `Integral` | Divisão inteira | `div`, `mod`, `quot`, `rem` |
| `Fractional` | Divisão real | `(/)`, `recip` |
| `Enum` | Enumeração/sequência | `succ`, `pred`, `[a..b]` |
| `Bounded` | Limites superior/inferior | `minBound`, `maxBound` |
| `Foldable` | Redução/dobramento | `foldr`, `foldl`, `sum`, `length` |
| `Functor` | Mapeamento sobre estrutura | `fmap` |

### Como ler restrições de tipo

```haskell
tem      :: Eq a => a -> [a] -> Bool
ordenar  :: Ord a => [a] -> [a]
maiorShow :: (Ord a, Show a) => a -> a -> String
maiorShow x y = show (max x y)
```

### Criando sua própria typeclass

#### Sintaxe completa

```haskell
--  ┌─ palavra-chave
--  │       ┌─ nome da typeclass (convenção: PascalCase)
--  │       │          ┌─ variável de tipo
class NomeDaClasse tipoVar where
  funcao1 :: tipoVar -> TipoRetorno     -- método obrigatório
  funcao2 :: tipoVar -> tipoVar -> Bool -- método obrigatório
  funcao3 :: tipoVar -> String          -- método com implementação padrão
  funcao3 _ = "(sem descrição)"         -- implementação padrão (opcional)
```

- Métodos **sem** implementação padrão → obrigatórios em toda instância
- Métodos **com** implementação padrão → podem ser sobrescritos, mas não precisam

#### Sintaxe com superclasse (herança)

```haskell
class Eq tipoVar => NomeDaClasse tipoVar where
  funcao1 :: tipoVar -> String
```

#### Sintaxe com múltiplas superclasses

```haskell
class (Eq a, Show a) => NomeDaClasse a where
  funcao1 :: a -> Bool
```

#### Sintaxe da instância

```haskell
instance NomeDaClasse MeuTipo where
  funcao1 x   = ...
  funcao2 x y = ...
  -- funcao3 não precisa ser definida se há padrão
```

#### Instância com restrição

```haskell
instance Show a => NomeDaClasse [a] where
  funcao1 xs = ...
```

#### Exemplo completo anotado

```haskell
class Resumivel a where
  resumir :: a -> String
  tamanho :: a -> Int
  vazio   :: a -> Bool
  vazio x  = tamanho x == 0   -- implementação padrão

data Pilha a = Pilha [a] deriving (Show)

instance Show a => Resumivel (Pilha a) where
  resumir (Pilha xs) = "Pilha: " ++ show xs
  tamanho (Pilha xs) = length xs
  -- vazio herdado do padrão

p1 = Pilha [1,2,3]
resumir p1  -- "Pilha: [1,2,3]"
tamanho p1  -- 3
vazio p1    -- False
```

### Implementando typeclasses padrão manualmente

```haskell
data Ponto = Ponto Double Double

instance Eq Ponto where
  (Ponto x1 y1) == (Ponto x2 y2) = x1 == x2 && y1 == y2

instance Show Ponto where
  show (Ponto x y) = "(" ++ show x ++ ", " ++ show y ++ ")"

instance Ord Ponto where
  compare (Ponto x1 y1) (Ponto x2 y2) =
    compare (x1^2 + y1^2) (x2^2 + y2^2)

Ponto 1 2 == Ponto 1 2  -- True
show (Ponto 3 4)         -- "(3.0, 4.0)"
Ponto 1 1 < Ponto 3 4   -- True
```

### Herança entre typeclasses

```haskell
-- Ord requer Eq
class Eq a => Ord a where
  compare :: a -> a -> Ordering

class Eq a => Hashable a where
  hash :: a -> Int
```

### Instâncias com restrições

```haskell
instance Show a => Descritivel [a] where
  descrever xs = "lista com " ++ show (length xs) ++ " elementos"

descrever [1,2,3]  -- "lista com 3 elementos"
```

### `deriving` vs instância manual

```haskell
data Direcao = Norte | Sul | Leste | Oeste
  deriving (Show, Eq, Ord, Enum, Bounded)

minBound :: Direcao  -- Norte
maxBound :: Direcao  -- Oeste
[Norte ..]           -- [Norte,Sul,Leste,Oeste]

-- Manual: você controla o comportamento
instance Show Direcao where
  show Norte = "N"
  show Sul   = "S"
  show Leste = "L"
  show Oeste = "O"
```

> 💡 **Regra de ouro:** use `deriving` para comportamento padrão e implemente manualmente quando precisar de controle sobre como o tipo se comporta.

---

## Monóides

Um **monóide** é qualquer tipo que possui duas coisas:
1. Uma **operação binária associativa** (`<>`) que combina dois valores
2. Um **elemento neutro** (`mempty`) que não altera o outro valor ao ser combinado

### A hierarquia: Semigroup e Monoid

```haskell
class Semigroup a where
  (<>) :: a -> a -> a

class Semigroup a => Monoid a where
  mempty :: a
```

### Monóides da biblioteca padrão

| Tipo | `mempty` | `(<>)` | Exemplo |
|---|---|---|---|
| `String` | `""` | concatenação | `"oi" <> " há"` → `"oi há"` |
| `[a]` | `[]` | concatenação | `[1,2] <> [3,4]` → `[1,2,3,4]` |
| `Sum Int` | `Sum 0` | soma | `Sum 3 <> Sum 4` → `Sum 7` |
| `Product Int` | `Product 1` | produto | `Product 3 <> Product 4` → `Product 12` |
| `Any` | `Any False` | `(\|\|)` | `Any True <> Any False` → `Any True` |
| `All` | `All True` | `(&&)` | `All True <> All False` → `All False` |
| `Maybe a` | `Nothing` | primeiro `Just` | `Nothing <> Just 3` → `Just 3` |

### As leis do Monóide

```haskell
(x <> y) <> z == x <> (y <> z)  -- associatividade
mempty <> x   == x               -- identidade à esquerda
x <> mempty   == x               -- identidade à direita
```

### `mconcat`

```haskell
mconcat :: Monoid a => [a] -> a
mconcat = foldr (<>) mempty

mconcat ["Haskell", " é", " legal"]  -- "Haskell é legal"
mconcat [[1,2], [3,4], [5,6]]        -- [1,2,3,4,5,6]
```

### Criando seu próprio Monóide

```haskell
newtype Maximo = Maximo { getMaximo :: Int } deriving (Show, Eq)

instance Semigroup Maximo where
  Maximo x <> Maximo y = Maximo (max x y)

instance Monoid Maximo where
  mempty = Maximo minBound

getMaximo (mconcat (map Maximo [3, 7, 1, 9, 4]))  -- 9
```

### Monóides e `foldMap`

```haskell
foldMap :: (Foldable t, Monoid m) => (a -> m) -> t a -> m

import Data.Monoid (Sum(..), All(..), Any(..))

foldMap Sum [1,2,3,4,5]          -- Sum {getSum = 15}
foldMap (All . (>0)) [1,2,3]     -- All {getAll = True}
foldMap (Any . even) [1,3,5,6]   -- Any {getAny = True}
foldMap show [1,2,3]             -- "123"
```

### `newtype` para múltiplos monóides

```haskell
import Data.Monoid

getSum     (foldMap Sum     [1..5])  -- 15
getProduct (foldMap Product [1..5])  -- 120
```

> 💡 **Por que Monóide importa?** Qualquer algoritmo que combina valores pode ser expresso com `foldMap` e um Monóide, tornando o código genérico e paralelizável (graças à associatividade).

---

## Funtores

Um **funtor** é qualquer estrutura que pode ser **mapeada** — permite aplicar uma função a seus valores internos sem alterar a forma da estrutura.

### A typeclass Functor

```haskell
class Functor f where
  fmap :: (a -> b) -> f a -> f b
--        └────────┘   └──┘   └──┘
--        função       entrada saída
```

- `f` é um **construtor de tipo** (como `[]`, `Maybe`)
- `<$>` é sinônimo infixo de `fmap`: `f <$> x` = `fmap f x`

### Funtores da biblioteca padrão

```haskell
fmap (+1) (Just 3)        -- Just 4
fmap (+1) Nothing         -- Nothing
fmap (*2) [1,2,3]         -- [2,4,6]
fmap (+1) (Right 3)       -- Right 4
fmap (+1) (Left "erro")   -- Left "erro"
fmap (+1) ("label", 4)    -- ("label", 5)
```

### As leis do Funtor

```haskell
fmap id x              == x             -- identidade
fmap (f . g) x         == fmap f (fmap g x)  -- composição
```

### Criando seu próprio Funtor

```haskell
data Rotulado r a = Rotulado r a deriving (Show)

instance Functor (Rotulado r) where
  fmap f (Rotulado r x) = Rotulado r (f x)

fmap (*2) (Rotulado "dobro" 5)  -- Rotulado "dobro" 10
```

### `fmap` vs `map`

```haskell
map  :: (a -> b) -> [a] -> [b]          -- só listas
fmap :: Functor f => (a -> b) -> f a -> f b  -- qualquer Functor

fmap (+1) (Just 5)   -- Just 6   (impossível com map)
fmap (+1) (Right 5)  -- Right 6  (impossível com map)
```

> 💡 **Intuição:** um funtor é uma "caixa" que preserva sua forma enquanto você transforma o que está dentro. `fmap` abre a caixa, aplica a função, e fecha de volta.

---

## Funtores Aplicativos

Um **funtor aplicativo** permite aplicar uma **função que também está dentro da estrutura**. Em Haskell, é a typeclass `Applicative`.

### O problema que Applicative resolve

```haskell
fmap (+1) (Just 3)   -- Just 4  (Functor consegue)
fmap (+)  (Just 3)   -- Just (+3)  ← função presa dentro do Maybe
-- Como aplicar Just (+3) ao Just 5? Precisa de <*>
```

### A typeclass Applicative

```haskell
class Functor f => Applicative f where
  pure  :: a -> f a
  (<*>) :: f (a -> b) -> f a -> f b
```

- `pure` eleva um valor puro para dentro da estrutura
- `<*>` (*ap*) aplica uma função embrulhada a um valor embrulhado

### Exemplo central: `Maybe`

```haskell
pure 5 :: Maybe Int     -- Just 5

Just (+3) <*> Just 5    -- Just 8
Nothing   <*> Just 5    -- Nothing  (função ausente)
Just (+3) <*> Nothing   -- Nothing  (valor ausente)
```

### Padrão `<$>` + `<*>`

```haskell
(+)  <$> Just 3 <*> Just 5        -- Just 8
(*)  <$> Just 4 <*> Just 6        -- Just 24
(+)  <$> Nothing <*> Just 5       -- Nothing

f3 a b c = a + b + c
f3 <$> Just 1 <*> Just 2 <*> Just 3   -- Just 6
f3 <$> Just 1 <*> Nothing <*> Just 3  -- Nothing
```

### Exemplo com tipo próprio: `Caixa`

```haskell
data Caixa a = Caixa a deriving (Show)

instance Functor Caixa where
  fmap f (Caixa x) = Caixa (f x)

instance Applicative Caixa where
  pure x              = Caixa x
  Caixa f <*> Caixa x = Caixa (f x)

(*) <$> Caixa 4 <*> Caixa 5  -- Caixa 20
```

### Applicative com listas

```haskell
-- <*> aplica todas as funções a todos os valores
[(+1), (*2)] <*> [10, 20, 30]
-- [11,21,31,20,40,60]

(,) <$> ["a","b"] <*> [1,2,3]
-- [("a",1),("a",2),("a",3),("b",1),("b",2),("b",3)]
```

### Funções auxiliares

```haskell
liftA2 (+) (Just 3) (Just 5)      -- Just 8
liftA2 (+) (Just 3) Nothing        -- Nothing
Just 3 *> Just 5                   -- Just 5  (descarta esquerda)
Just 3 <* Just 5                   -- Just 3  (descarta direita)
```

### Applicative vs Functor vs Monad

```haskell
fmap (+1) (Just 3)                        -- Just 4  (Functor)
Just (+1) <*> Just 3                      -- Just 4  (Applicative)
Just 3 >>= (\x -> Just (x + 1))           -- Just 4  (Monad)

-- Só Monad pode ramificar com base no valor:
Just 3 >>= (\x -> if x > 0 then Just x else Nothing)
```

> 💡 **Intuição:** `Applicative` é quando a função também está dentro de uma caixa — você combina duas caixas em uma. Útil para encadear operações que podem falhar (`Maybe`), acumular erros (`Either`), ou gerar combinações (`[]`).

## Mônadas

Uma **mônada** é um `Applicative` que sabe **encadear operações que produzem estruturas**. A diferença crucial: o resultado de uma etapa pode determinar a estrutura da próxima.

### A typeclass Monad

```haskell
class Applicative m => Monad m where
  return :: a -> m a
  (>>=)  :: m a -> (a -> m b) -> m b
--          └──┘   └────────┘
--         mônada  função que retorna nova mônada
```

- `>>=` (*bind*) extrai o valor e o passa para uma função que produz uma nova estrutura
- `>>` ignora o valor da esquerda: `m >> n = m >>= \_ -> n`

### O problema que Monad resolve

```haskell
-- Applicative: estruturas fixas e independentes
(+) <$> Just 3 <*> Just 5   -- Just 8  (não depende do valor)

-- Monad: estrutura pode depender do valor
Just 3    >>= (\x -> if x > 0 then Just (x*2) else Nothing)  -- Just 6
Just (-3) >>= (\x -> if x > 0 then Just (x*2) else Nothing)  -- Nothing
```

### Mônada `Maybe`: computações que podem falhar

```haskell
safeDiv :: Int -> Int -> Maybe Int
safeDiv _ 0 = Nothing
safeDiv x y = Just (x `div` y)

-- Encadeando: para no primeiro Nothing
Just 10 >>= safeDiv 100 >>= safeDiv 5  -- Just 2
Just 0  >>= safeDiv 100 >>= safeDiv 5  -- Nothing

-- Sem mônada, equivale a:
case safeDiv 100 10 of
  Nothing -> Nothing
  Just r1 -> case safeDiv r1 5 of
    Nothing -> Nothing
    Just r2 -> Just r2
```

### Notação `do`

Açúcar sintático sobre `>>=` que torna o código sequencial mais legível:

```haskell
-- Com >>=:
buscarEndereco uid =
  buscarUsuario uid >>= \usuario ->
  buscarCidade (cidade usuario) >>= \cid ->
  Just (nome cid ++ ", " ++ pais cid)

-- Com notação do (equivalente exato):
buscarEndereco uid = do
  usuario <- buscarUsuario uid
  cid     <- buscarCidade (cidade usuario)
  return (nome cid ++ ", " ++ pais cid)
```

#### Anatomia da notação `do`

```haskell
resultado = do
  x <- acao1      -- x <- m  equivale a  m >>= \x -> ...
  y <- acao2 x
  let z = x + y   -- let sem extração (valor puro)
  acao3 z         -- última linha: tipo de retorno de todo o bloco
```

### Mônada `[]`: computações não-determinísticas

```haskell
[1,2,3] >>= \x -> [x, x*10]  -- [1,10,2,20,3,30]  (= concatMap)

pares = do
  x <- [1,2,3]
  y <- ["a","b"]
  return (x, y)
-- [(1,"a"),(1,"b"),(2,"a"),(2,"b"),(3,"a"),(3,"b")]

-- Equivale à compreensão de listas:
[(x,y) | x <- [1,2,3], y <- ["a","b"]]

-- Com guarda:
import Control.Monad (guard)
pitagoricos = do
  a <- [1..20]; b <- [a..20]; c <- [b..20]
  guard (a^2 + b^2 == c^2)
  return (a, b, c)
-- [(3,4,5),(5,12,13),(6,8,10),(8,15,17),(9,12,15),(12,16,20)]
```

### Mônada `Either`: computações com erro descritivo

```haskell
type Erro = String

validarIdade :: Int -> Either Erro Int
validarIdade n
  | n < 0    = Left "Idade não pode ser negativa"
  | n > 150  = Left "Idade improvável"
  | otherwise = Right n

validarNome :: String -> Either Erro String
validarNome "" = Left "Nome não pode ser vazio"
validarNome n  = Right n

criarPessoa :: String -> Int -> Either Erro Pessoa
criarPessoa nome idade = do
  n <- validarNome nome
  i <- validarIdade idade
  return (Pessoa n i)

criarPessoa "Ana" 25    -- Right (Pessoa "Ana" 25)
criarPessoa "" 25       -- Left "Nome não pode ser vazio"
criarPessoa "Ana" (-5)  -- Left "Idade não pode ser negativa"
```

### Mônada `IO`: efeitos colaterais controlados

```haskell
getLine  :: IO String
putStrLn :: String -> IO ()
readFile :: FilePath -> IO String

main :: IO ()
main = do
  putStrLn "Qual é o seu nome?"
  nome <- getLine
  putStrLn ("Olá, " ++ nome ++ "!")

-- IO torna efeitos explícitos na assinatura:
soma       :: Int -> Int -> Int      -- pura
somaComLog :: Int -> Int -> IO Int   -- impura
somaComLog x y = do
  putStrLn ("Somando " ++ show x ++ " e " ++ show y)
  return (x + y)
```

### Funções úteis da biblioteca de mônadas

```haskell
import Control.Monad

when   (x > 0)   (putStrLn "positivo")   -- executa se True
unless (null xs) (putStrLn "não vazio")  -- executa se False

mapM_ print [1,2,3]                       -- aplica e descarta resultados
resultados <- mapM safeDiv [10, 20, 30]   -- aplica e coleta resultados

sequence [Just 1, Just 2, Just 3]   -- Just [1,2,3]
sequence [Just 1, Nothing, Just 3]  -- Nothing

join (Just (Just 3))  -- Just 3
join [[1,2],[3,4]]    -- [1,2,3,4]
```

### As leis da Mônada

```haskell
return a >>= f       == f a           -- identidade à esquerda
m >>= return         == m             -- identidade à direita
(m >>= f) >>= g      == m >>= (\x -> f x >>= g)  -- associatividade
```

### A hierarquia completa

```
Functor          →  fmap   transforma o valor, estrutura fixa
  └─ Applicative →  <*>    combina estruturas independentes
       └─ Monad  →  >>=    encadeia, estrutura depende do valor
```

```haskell
fmap (+1) (Just 3)               -- Just 4  (Functor)
pure (+1) <*> Just 3             -- Just 4  (Applicative)
Just 3 >>= \x -> return (x+1)   -- Just 4  (Monad)

-- Só Monad ramifica com base no valor:
Just 3 >>= \x -> if even x then Just x else Nothing  -- Nothing
Just 4 >>= \x -> if even x then Just x else Nothing  -- Just 4
```

> 💡 **Intuição:** se `Functor` é transformar o conteúdo de uma caixa e `Applicative` é combinar caixas independentes, `Monad` é abrir uma caixa, olhar o que está dentro, e *decidir qual caixa criar a seguir*. É isso que `IO` usa para sequenciar efeitos colaterais de forma segura.
