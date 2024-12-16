- Como definir um problema?
Todo problema é composto por uma entrada de dados e uma pergunta para respondermos.
- Quais são os tipos de problema?
	- Otimização: consiste em maximizar ou minimizar uma solução, dentre todas as possiveis
	- Decisão: 
---
##### Tipos de problemas em grafos
###### Otimização:
- Conjunto independente(Otimização - maximização):
	- Recebe como dado de entrada um [grafo] e a questão é [determinar o conjunto independente máximo de G(grafo)]
	- É um subconjunto onde qualquer par de vertices nesse grafo não é vizinho.
	- Um unico vértice é um conjunto independente
- Cobertura por vertices(Otimização - minimização):
	- Recebe como dado de entrada um [grafo] e a questão é [determinar a cobertura mínima de arestas de G por vértices]
	- É um conjunto de vértices onde todas as arestas devem possuir pelo menos um vertice ligado a ela.
- O conjunto independente é complementar a cobertura por vertices, ou seja resolver um e pelo menos tao dificil quanto resolver o outro
- Podemos considerar que minimização e maximização tem uma relação muito forte, com uma mudança na pergunta
###### Decisão:
Qualquer problema de otimização tem um problema de decisão associado.
Ou seja podemos formular um problema que seja resolvido em termos de "Sim" ou "Não".
Devendo ter o mesmo conjunto de entrada, mas acrescentando um valor inteiro K.
Reformulando teremos algo como "existe uma solução é >= k" ou "existe uma solução é =< k"

---
###### Classe P

A classe P de problemas (de decisão) corresponde exatamente aos problemas trataveis

P: Problemas que podem ser resolvidos em tempo polinomial em uma maquina de turing deterministica
Ex: Caminho minimo (decisao)
	Dados: Grafo G, inteiro K, vertices v1 e v2 que pertencem ao grafo
	Pergunta: G possui caminho de v1 ate a v2 com tamanho =< K?

Caminho minimo é um problema em P pois sao conhecidos algoritimos eficientes para solucionar ele

###### Certificados

Um certificado para um problema de decisao é algo que, quando valido, atesta a solução do problema. O certificado pode ser tanto para sim, quanto para nao.

Ex: Conjunto independente
O certificado seria um subconjunto de vertices do grafo

Grafos Eulerianos consite em dado um grafo G, ao sair de um vértice v1 e voltar para ele, passando por todas as arestas exatamente uma vez.
Um grafo é euleriano sse todos os vertices possuem grau par.


###### Classe NP
São os problemas que podem ser certificados em tempo polinomial, e eventualmente resolvidos por uma maquina de turing NAO deterministica.

