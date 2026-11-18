# Roteiro de prova por tema (Algoritmos em Grafos, P2)

Para que serve: dizer, para cada tema, QUE TIPOS de questão podem cair e QUAL a ordem de passos para resolver. Os detalhes e modelos de resposta estão em `formulario-metodos-grafos.md`.
Formato provável da P2 (a partir da P1): 5 questões de 2,0; as de execução têm 4 itens de 0,5 (determinar, preencher tabela, justificar, desenhar); 1 questão de V/F com 4 itens (certo +0,5, errado −0,25, sem justificar); 1 questão de escrever algoritmo ou modelar.

---

## 1. Fluxo em redes

Tipos de questão: (a) modelar; (b) executar Ford–Fulkerson com tabela; (c) classificar um fluxo (maximal, máximo, nem um nem outro); (d) corte mínimo; (e) Ford–Fulkerson contra Edmonds–Karp.

Ordem de passos para MAXIMIZAR o fluxo:
1. Modelar: super-origem s0 (várias fábricas) e super-destino t (várias lojas); capacidade de vértice = dividir em entrada e saída; caminhos disjuntos em arestas = capacidade 1 em toda aresta.
2. Comece com fluxo 0 em todas as arestas.
3. Monte a rede RESIDUAL: para cada aresta, frente (c − f, se > 0) e volta (f, se > 0).
4. BFS a partir de s na residual (frente e volta).
5. Se alcançou t: pegue o caminho, empurre o GARGALO (menor capacidade do caminho), atualize f e volte ao passo 3. Anote na tabela: iteração, caminho, gargalo, valor do fluxo.
6. Se NÃO alcançou t: o fluxo é máximo. S = vértices alcançados na última BFS. Corte mínimo = arestas ORIGINAIS que saem de S para fora; some as capacidades e confira que dá |f|.

Cuidados:
- Gargalo é o menor valor de um caminho. Não confundir com as arestas do corte.
- A residual vem ANTES da BFS; o corte só sai da última BFS.
- A BFS sem as arestas de volta pode parar cedo demais (fluxo maximal e não máximo).
- Corte conta só as arestas de S para fora; as que entram em S não contam.
- Para provar um valor máximo: um fluxo (com conservação) mais um corte de mesma capacidade.

---

## 2. Emparelhamentos

Tipos de questão: (a) classificar M (maximal, máximo, perfeito); (b) método húngaro; (c) V/F e provas (Berge, Hall, cobertura); (d) modelar alocação como bipartido; (e) reduzir a fluxo.

Como resolver:
- Classificar M: liste cobertos e livres; verifique se alguma aresta liga dois livres (não maximal). Se maximal, compare com o limite superior ou procure caminho M-aumentante.
- Húngaro: para cada livre de X (ordem do enunciado), monte a árvore alternante (de X por arestas fora de M, de Y só pela aresta de M). Achou livre de Y: M′ = M Δ P e |M′| = |M| + 1. Árvore fechou: S e T; |N(S)| = |S| − 1. No final: ν = |M|, Hall com o S, cobertura C = (X \ S) ∪ T com |C| = |M|.
- Hall: S ⊆ X com |N(S)| < |S| impede cobrir X.
- Berge: M é máximo se e só se não há caminho M-aumentante.
- Modelar: vértices de um lado, vértices do outro, aresta quando "aceita"; alocação completa = emparelhamento perfeito.
- Reduzir bipartido a fluxo: s → X com capacidade 1, X → Y (as arestas do grafo) com capacidade 1, Y → t com capacidade 1. O fluxo inteiro máximo é ν(G), e as arestas X → Y com fluxo 1 formam o emparelhamento (integralidade do fluxo).

---

## 3. Grafos Eulerianos e Carteiro Chinês

Tipos de questão: (a) para quais parâmetros Kn, Km,n, Qk, Wn, Petersen são eulerianos; (b) Hierholzer; (c) Carteiro fechado; (d) Carteiro com partida e chegada fixas (caso 15b); (e) provas curtas (número par de ímpares).

Passos do Carteiro fechado: ímpares; caminhos mínimos entre os pares; listar TODOS os emparelhamentos perfeitos dos ímpares; escolher o de menor soma; duplicar os caminhos; conferir graus pares; custo = soma das arestas + extra; escrever o passeio.
Partida e chegada fixas: X de custo 0 ligando os extremos; recalcule quem é ímpar (regra: ímpares com o status dos extremos trocado); emparelhe; duplique; circuito com X; retire X e gire o circuito.
Critérios: circuito euleriano se conexo e todos os graus pares; trilha aberta se exatamente 2 graus ímpares.
Hierholzer: menor vizinho livre (por ARESTA livre), trava no início; novo circuito a partir do PRIMEIRO vértice do circuito, na ordem percorrida, com aresta livre; encaixa.

---

## 4. Caixeiro Viajante (a preencher com mais exemplos)

Tipos de questão: (a) vizinho mais próximo (NN); (b) Held–Karp; (c) árvore dupla e Christofides; (d) 2-opt; (e) V/F.

- NN: de cada cidade vá à mais próxima ainda não visitada e volte ao início. Heurística gulosa, sem boa garantia.
- Held–Karp: g(i, ∅) = c_i1; g(i, C) = min sobre j em C de c_ij + g(j, C \ {j}); tabela por |C| = 0, 1, 2…; resposta g(1, tudo menos 1); reconstruir pelo j que dá o mínimo. Tempo O(n²·2ⁿ).
- Árvore dupla: MST, duplicar as arestas (circuito euleriano; na prática pré-ordem), atalhos. Custo ≤ 2·MST ≤ 2·ótimo. Exige desigualdade triangular.
- Christofides: MST, ímpares da árvore, emparelhamento perfeito mínimo entre eles, circuito euleriano, atalhos. Garantia 1,5·ótimo.
- 2-opt: remover duas arestas não adjacentes e reconectar da única outra forma que dá ciclo; repetir até ótimo local (não é necessariamente global).
- V/F importantes: MST ≤ ótimo; se métrica, ótimo ≤ 2·MST.

---

## 5. Coloração (o professor resolve na sexta)

A preencher depois da aula.
