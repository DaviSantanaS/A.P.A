## 1. Prova Direta

### O que é uma Prova Direta?

Uma prova direta é um método onde partimos de hipóteses ou premissas conhecidas e, através de uma sequência de passos lógicos, chegamos à conclusão desejada. É a forma mais básica e intuitiva de prova.

### Como Funciona?

- **Início**: Partimos de informações ou axiomas que já sabemos serem verdadeiros.
- **Processo**: Usamos regras de lógica e matemática para manipular essas informações.
- **Conclusão**: Chegamos à afirmação que queríamos provar.

### Exemplo 1: Provar que a soma de dois números pares é sempre par.

**Passo 1**: Defina dois números pares. Um número par é divisível por 2, então podemos escrever:
	
	Seja a = 2k e b = 2m, onde k e m são inteiros
	
**Passo 2**: Some os dois números:
	
	a+b = 2k + 2m
	
**Passo 3**: Fator comum:
	
	 a+b = 2(k+m)
	
**Passo 4**: Conclusão:
	
	a + b é múltiplo de 2, portanto, é par.

### Exemplo 2: Provar que o produto de dois números ímpares é ímpar.

**Passo 1**: Defina dois números ímpares. Um número ímpar pode ser escrito como 2n+1:
	
	Seja a = 2k + 1 e b = 2m + 1, onde k e m são inteiros.
	
**Passo 2**: Multiplique os dois números:
	
	 a×b = (2k + 1) (2m + 1)
	
**Passo 3**: Expanda o produto:
	
	 a×b = 4km + 2k + 2m + 1
	
**Passo 4**: Simplifique:
	
	 a×b = 2 (2km + k +  m) + 1
	
**Passo 5**: Como 2km + k + m é inteiro, podemos chamar de nnn
	
	 a×b = 2n + 1
	
**Passo 6**: Conclusão:
	
	 O produto é da forma 2n + 1, logo, é ímpar.


---

## 2. Prova por Contradição

### O que é uma Prova por Contradição?

Na prova por contradição, assumimos que a afirmação que queremos provar é falsa. A partir dessa suposição, mostramos que isso leva a uma contradição lógica ou a um absurdo, o que implica que a suposição inicial é falsa, portanto, a afirmação original é verdadeira.

### Como Funciona?

- **Suposição Inicial**: Assumimos que a afirmação é falsa.
- **Desenvolvimento**: Usamos essa suposição para deduzir consequências.
- **Contradição**: Chegamos a uma afirmação que contradiz um fato conhecido ou a própria suposição.
- **Conclusão**: Portanto, a suposição está errada, e a afirmação original é verdadeira.

### Exemplo 1: Provar que não existe o menor número racional positivo.

**Passo 1**: Suponha que existe um menor número racional positivo rrr.
	
**Passo 2**: Considere r/2, que também é um número racional positivo menor que r.
	
**Passo 3**: Contradição:
	
	 r/2 < r, o que contradiz a suposição de que r é o menor número racional positivo.

**Conclusão**: Não existe o menor número racional positivo.

### Exemplo 2: Provar que há infinitos números primos.

**Passo 1**: Suponha que existe um número finito de números primos: p1​,p2​,p3​,...,pn​​.
	
**Passo 2**: Considere o número Q = p1​ × p2 ​× p3 ​×...× pn ​+ 1
	
**Passo 3**: Analisando Q:
	
	  Q não é divisível por nenhum dos primos pi​, pois resta 1 em cada divisão.
	
**Passo 4**: Portanto, Q é primo ou tem um fator primo não listado.

**Contradição**: Isso contradiz a suposição de que listamos todos os primos.

**Conclusão**: Existem infinitos números primos.


## 3. Prova por Indução Matemática

### O que é Indução Matemática?

A indução matemática é um método de prova usado para mostrar que uma afirmação é verdadeira para todos os números naturais. Funciona como um efeito dominó: se conseguimos provar que a primeira peça cai (caso base) e que uma peça derruba a próxima (passo de indução), todas as peças cairão (a afirmação é verdadeira para todos os nnn).

### Como Funciona?

1. **Caso Base**: Provar que a afirmação é verdadeira para n=1 (ou outro ponto de partida adequado)
    
2. **Hipótese de Indução**: Assumir que a afirmação é verdadeira para n=k.
    
3. **Passo de Indução**: Mostrar que, se a afirmação é verdadeira para n=k, então é verdadeira para n = k + 1.
    
4. **Conclusão**: Assim, a afirmação é verdadeira para todos os números naturais n.
    

### Exemplo 1: Provar que 2^n ≥ n + 1 para todo n ≥ 1. 

**Caso Base** (n = 1):

- 2^1 = 2
- 1+1=2
- Portanto, 2   ≥2 é verdadeiro.

**Hipótese de Indução**:

- Suponha que 2^k   ≥ k + 1 é verdadeiro para algum k   ≥ 1.

**Passo de Indução**:

- Queremos mostrar que 2 ^(k+1)   ≥ (k + 1) + 1.
    
- Observe que 2^(k+1) = 2 x 2^k .
    
- Pela hipótese de indução, 2^k   ≥k + 1, então:
    
		2^(k + 1) = 2 x 2^k   ≥ 2(k + 1)
    
- Portanto:
    
		2^(k + 1)   ≥ 2k + 2
    
- Note que 2k + 2   ≥k + 2  para k  ≥1.
    
- Assim:
    
		2^(k + 1)   ≥ 2k + 2
    

**Conclusão**:

- A afirmação é verdadeira para n = k + 1.

- Portanto, por indução,  2^n   ≥n+1 para todo n   ≥1.


### Exemplo 2: Provar que a soma dos n primeiros números ímpares é n^2.

**Caso Base** (n = 1):

- Soma dos primeiros 1 número ímpar: 1
    
- n^2 = 1^2 =1
    
- Portanto, 1 = 1, verdadeiro.


**Hipótese de Indução**:

- Suponha que a soma dos primeiros k números ímpares é k^2.

**Passo de Indução**:

- Queremos mostrar que a soma dos primeiros k + 1 números ímpares é (k + 1)^2.
    
- Soma até k + 1:
    
	    S (k+1) = S (k) + próximo número ímpar
    
- O (k + 1) ésimo número impar é 2(k + 1) - 1 = 2k + 1.
    
- Portanto:
	
		S (k+1) = k^2 + (2k + 1)
    
- Simplificando:
    
	    S (k+1) = k^2 + 2k + 1 = (k + 1)^2
    

**Conclusão**:

- A afirmação é verdadeira para n = k + 1.
- Portanto, por indução, a soma dos n primeiros números ímpares é n^2.
## OFF topic
###### Funções

- **Injetiva (Um-para-Um)**: Cada elemento do domínio mapeia para um elemento distinto do contradomínio.
- **Sobrejetiva (Sobre)**: O contradomínio é totalmente coberto pela função.
- **Bijetiva**: Função que é injetiva e sobrejetiva.

###### Conjuntos e Operações

- **União (U)**: Todos os elementos que estão em pelo menos um dos conjuntos.
- **Interseção (∩)**: Elementos comuns a ambos os conjuntos.
- **Diferença**: Elementos que estão em um conjunto e não no outro.
###### Lei da Contraposição
- A **Lei da Contraposição** afirma que uma implicação é logicamente equivalente à sua contrarrecíproca. A contrarrecíproca de uma proposição condicional P  ⟹  Q é ¬Q  ⟹  ¬P.
- Como exemplo teriamos: (Se está chovendo, então a grama está molhada) ⟹ (Se a grama não está molhada, então não está chovendo)

###### Lei da Dupla Negação
- ¬(¬P) ≡ P

###### Lei da Distributividade
A **Lei da Distributividade** permite distribuir operações lógicas da mesma forma que fazemos com operações aritméticas.

- **Forma geral para AND sobre OR**:  
		P ∧ ( Q ∨ R) ≡ (P ∧ Q) ∨ (P ∧ R)
- **Forma geral para OR sobre AND**:  
	    P ∨ (Q ∧ R) ≡ (P ∨ Q) ∧ (P ∨ R)
    
- **Exemplo**  : Distribuindo a conjunção em uma disjunção, "Estou em casa **e** (estou lendo **ou** assistindo TV)" é equivalente a "(Estou em casa **e** lendo) **ou** (Estou em casa **e** assistindo TV)."

##### Leis de Morgan
###### Primeira Lei de Morgan

- A primeira lei diz que negar duas proposições ligadas com **“e”** – ou seja, uma conjunção – é o mesmo que negar duas proposições e ligá-las com **“ou”,** ou seja, transformá-las em uma disjunção. leis de morgan Considere que “p” e “q” são duas proposições. Simbolicamente a primeira lei pode ser  representada por: ~ (p ? q) = (~ p) ? (~ q) Em outras palavras: Não (p e q) é igual a (não p) ou (não q). Exemplos: Sendo “p” igual a “João vai ao futebol”. Sendo “q” igual a “Ana vai ao cinema”. A primeira Lei de Morgan aplicada às proposições ficará: Não (João vai ao futebol e Ana vai ao cinema) é o mesmo que (João não vai ao futebol ou Ana não vai ao cinema). Resumindo: negar que “João vai ao futebol e Ana vai ao cinema” é o mesmo que afirmar que “Ou João não vai ao futebol ou Ana não vai ao cinema”.

###### Segunda Lei de Morgan

- A segunda lei diz que negar duas proposições ligadas por “ou” é o mesmo que negar as duas proposições e juntá-las com “e”. A representação simbólica é a seguinte: ~ (p ? q) = (~ p) ? (~ q) Em outras palavras: Não (p ou q) é igual a (não p) e (não q). Exemplos: Não (João vai ao futebol ou Ana vai ao cinema) é o mesmo que (João não vai ao futebol e Ana não vai ao cinema). Ou seja,  negar que “João vai ao futebol ou Ana vai ao cinema” é igual a afirmar que "João não vai ao futebol e Ana não vai ao cinema”. leis de morgan
