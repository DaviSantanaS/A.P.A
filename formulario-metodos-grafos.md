# Formulário de Métodos — Algoritmos em Grafos (IC/UFF, Prof. Fábio)

Objetivo: entender cada método, praticar N exercícios e escrever respostas nota 10.
Como usar: leia a receita do tema, resolva o exercício seguindo os passos na ordem e confira com o "modelo de resposta".
Estado: Tema 1 (Emparelhamentos) em construção (Ex. 1 a 4 feitos). Temas 2 a 5 serão preenchidos conforme formos resolvendo.

---

## 0. Notação e definições (vale para tudo)

- |V(G)| = número de vértices. |M| = número de arestas de M.
- ν(G) (letra grega "ni", não é um V) = tamanho do emparelhamento máximo de G.
- N(v) = vizinhos de v. N(S) = união dos vizinhos dos vértices de S.
- Emparelhamento M: conjunto de arestas sem vértice repetido.
- Vértice coberto por M: aparece em alguma aresta de M. Livre: não aparece.
- Maximal: nenhuma aresta de G liga dois vértices livres (não dá para acrescentar aresta).
- Máximo: |M| = ν(G) (maior possível). Todo máximo é maximal; a volta é falsa.
- Perfeito: M cobre todos os vértices.
- Caminho M-aumentante P: começa e termina em vértices livres e alterna "fora de M, dentro de M, fora de M...". Com 2t+1 arestas tem t+1 fora de M e t dentro.
- M Δ P (diferença simétrica): arestas em exatamente um dos dois. Na prática: as arestas de P que estão em M SAEM, as de P que não estão em M ENTRAM, as de M fora de P FICAM. Resultado: |M Δ P| = |M| + 1.
- Berge: M é máximo ⇔ G não tem caminho M-aumentante.
- Limite superior: |M| ≤ ⌊|V|/2⌋. Em bipartido também |M| ≤ min(|X|, |Y|).
- Hall (bipartido X, Y): existe emparelhamento que cobre X ⇔ para todo S ⊆ X, |N(S)| ≥ |S|. Se algum S tem |N(S)| < |S|, nenhum emparelhamento cobre X.
- Cobertura por vértices: conjunto C de vértices que toca TODAS as arestas. Para todo emparelhamento M, |M| ≤ |C| (cada aresta de M usa uma ponta diferente de C).

---

## 1. Emparelhamentos

### 1.1 Classificar M como maximal / máximo / nem um nem outro

Passo 1. Escreva os cobertos e os livres como conjuntos.
Passo 2. Teste de maximal: para cada livre v, escreva N(v) e marque cada vizinho como livre ou coberto.
  - Se alguma aresta liga dois livres: M NÃO é maximal. Essa aresta e cabe em M; M ∪ {e} é maior (é um caminho aumentante de comprimento 1).
  - Se nenhuma liga: M é maximal.
Passo 3. Se M é maximal, é máximo?
  a) Compare |M| com um limite superior (⌊|V|/2⌋, ou min(|X|,|Y|) em bipartido). Se |M| = limite, é máximo. Escreva o argumento do limite.
  b) Se |M| < limite, "menor que o limite" NÃO prova que não é máximo. Procure um caminho aumentante: parta de um livre, alterne fora/dentro de M, termine em outro livre. Achou: M não é máximo; calcule M′ = M Δ P e |M′|.
Passo 4. Conclusão em uma frase: "M é maximal, mas não máximo" / "nem maximal nem máximo" / "máximo (e portanto maximal)".

Modelo de resposta (exemplo: grade 3×3, M₁ = {25, 47, 69}):
> Cobertos: {2,4,5,6,7,9}. Livres: {1,3,8}. N(1)={2,4}, N(3)={2,6}, N(8)={5,7,9}, todos cobertos, então nenhuma aresta liga dois livres: M₁ é maximal. P = 1–2–5–8 é M₁-aumentante (12 ∉ M₁, 25 ∈ M₁, 58 ∉ M₁; pontas livres). M′ = M₁ Δ P = {12, 58, 47, 69}, vértices distintos, |M′| = 4 > 3. Logo M₁ não é máximo. Conclusão: maximal, mas não máximo.

Outro caso (M₂ = {12,56,89}): livres {3,4,7}; a aresta 47 liga dois livres, então não é maximal; M₂ ∪ {47} é maior. Como todo máximo é maximal, também não é máximo.
Caso máximo (M₃ = {12,36,45,78}): um livre só (9); ν(G) ≤ ⌊9/2⌋ = 4 = |M₃|, logo máximo.

### 1.2 Método Húngaro (bipartido X, Y)

Regras do enunciado típico: livres de X em ordem alfabética; vizinhos em ordem crescente.

Cada iteração (repita até todos os livres de X terem sido tentados):
1. Raiz = próximo livre de X.
2. Árvore alternante:
   - De um vértice de X, siga arestas FORA de M até os vizinhos em Y.
   - De um vértice de Y: se é LIVRE, PARE (achou caminho aumentante). Se é COBERTO, siga SÓ a aresta de M dele até o par em X e continue dali.
   - Cada vértice entra uma vez só na árvore.
   - Desenhe com legenda de cores (azul = fora de M, vermelho = em M).
3. Desfecho:
   - Achou livre de Y: destaque P (só o ramo da raiz até o livre, escolha o menor livre). M′ = M Δ P, confira |M′| = |M| + 1. Próxima iteração com M′.
   - A árvore fechou sem livre de Y: anote S (vértices de X da árvore) e T (vértices de Y da árvore). Teremos |N(S)| = |T| = |S| − 1.

Como escrever cada iteração:
> Iteração k, raiz r. M atual = {…}. Árvore (desenho). Resultado: achou P = … e M′ = … com |M′| = …; OU a árvore fechou com S = …, T = ….

Conclusão (quando não restam raízes a tentar):
1. ν(G) = |M| final.
2. Hall: S da árvore que fechou, com |N(S)| < |S|.
3. Cobertura C = (X \ S) ∪ T; confira aresta por aresta que toca todas. Se mais de uma raiz fechou, use a união das árvores. |C| = |M| prova que M é máximo (|M| ≤ ν ≤ |C| = |M|).

Resultado do Ex. 3 (grafo X={a..f}, Y={1..6}; M = {a1,c2,d3,e4}):
- It. 1, raiz b: árvore b—1~a—2~c, ramos c—3~d e c—4~e; d—5 livre. P = b–1–a–2–c–3–d–5. M′ = {b1,a2,c3,d5,e4}.
- It. 2, raiz f: f → (2~a—1~b) e (4~e—3~c); nenhum livre de Y. S = {a,b,c,e,f}, T = {1,2,3,4}, |N(S)| = 4 < 5.
- ν(G) = 5; cobertura C = {d,1,2,3,4}.

### 1.3 Provas e V/F do Ex. 2 (modelos)

2(a) VERDADEIRA: M maximal ⇒ |M| ≥ ν(G)/2.
> Seja M* máximo. (1) Toda aresta de M* tem uma ponta coberta por M; senão M ∪ {e} seria emparelhamento, contra a maximalidade. (2) Arestas diferentes de M* usam pontas cobertas distintas (M* é emparelhamento). (3) M cobre 2|M| vértices. Logo |M*| ≤ 2|M|, ou seja, |M| ≥ ν(G)/2.
(Justo: no caminho a–b–c–d, M = {bc} é maximal com |M| = 1 = ν/2.)

2(b) FALSA: G com emparelhamento perfeito ⇒ todo maximal é perfeito.
> Contraexemplo: caminho a–b–c–d tem perfeito {ab, cd}; M = {bc} é maximal (N(a)={b}, N(d)={c} cobertos) mas deixa a e d livres.

2(c) VERDADEIRA: componentes de M Δ M′ são caminhos ou ciclos pares.
> Cada vértice é tocado por no máximo 1 aresta de M e 1 de M′, então tem grau ≤ 2 em M Δ M′: sem ramificação, só caminhos e ciclos. Em vértice de grau 2, uma aresta é de M e outra de M′ (duas de M não podem compartilhar vértice), então as arestas alternam. Um ciclo alternante tem metade de cada, logo comprimento par.

2(d) Berge (M máximo ⇔ sem caminho M-aumentante).
> (⇒, contrapositiva) Se existe P aumentante, M Δ P é emparelhamento (pontas livres, meio troca as arestas) com |M|+1 arestas, então M não é máximo.
> (⇐, ideia; revisar com calma) Se M não é máximo, tome M* máximo. Em M Δ M*, as componentes são caminhos e ciclos pares alternantes; como |M*| > |M|, alguma componente-caminho tem uma aresta de M* a mais; suas pontas são livres em M, então é M-aumentante.

### 1.4 Modelar um problema de alocação como emparelhamento (Ex. 4)

Receita:
1. (a) Modelagem. X = um lado (monitores), Y = outro (disciplinas). Aresta x–y quando x ACEITA y (use o verbo do enunciado; ex.: "aceita", não "ministra"). Alocação válida = emparelhamento (cada monitor em uma disciplina, cada disciplina com um monitor). Alocação completa = emparelhamento perfeito (aqui |X| = |Y| = 5). Preferências entre monitores não entram no grafo.
2. (b) "É possível alocar todos?" Use Hall: ache S ⊆ X com |N(S)| < |S|. Não existe emparelhamento que cubra X, então a alocação completa é impossível.
3. (b) "Maior número possível": (i) exiba um emparelhamento do tamanho que você afirma; (ii) prove que não dá para mais, com uma cobertura C de mesmo tamanho (|M| ≤ |C|). Com o S e o T da árvore que fechou: C = (X \ S) ∪ T.
4. (c) "Exiba uma alocação completa" depois de mudar o grafo: parta do M do item (b), pegue o livre de X como raiz, monte a árvore alternante até um livre de Y, escreva P marcando ∉M / ∈M, calcule M′ = M Δ P e confira que cada vértice aparece uma vez só.

Resultado do Ex. 4 (Ana: Cálculo, Álgebra / Bruno: Álgebra / Carla: Cálculo, Álgebra / Diego: Cálculo, Álgebra, Grafos / Eva: Física, Programação, Grafos):
- (b) S = {Ana, Bruno, Carla}, N(S) = {Cálculo, Álgebra}, |N(S)| = 2 < 3. Não dá para alocar os 5. M = {Ana–Cálculo, Bruno–Álgebra, Diego–Grafos, Eva–Programação} tem 4; cobertura C = {Diego, Eva, Cálculo, Álgebra} toca todas as arestas e |C| = 4, então ν = 4.
- (c) Com Bruno–Física: P = Carla – Cálculo ~ Ana – Álgebra ~ Bruno – Física. M′ = {Carla–Cálculo, Ana–Álgebra, Bruno–Física, Diego–Grafos, Eva–Programação}, |M′| = 5.
- O enunciado não fixa a ordem dos vizinhos, então qualquer P vale. Em ordem alfabética sairia P = Carla – Álgebra ~ Bruno – Física e M′ = {Ana–Cálculo, Carla–Álgebra, Bruno–Física, Diego–Grafos, Eva–Programação}.

### 1.5 Armadilhas já encontradas
- Ter vértices livres não torna M não maximal; o que importa é existir aresta ENTRE dois livres. Quem exige cobrir tudo é o perfeito.
- |V|/2 é teto para |M|; "|M| ≥ ν/2" é outro enunciado (2a). Não misturar.
- |M| conta arestas; "cobrir" conta vértices. M cobre 2|M| vértices.
- "Menor que o limite" não prova não-máximo; precisa de caminho aumentante.
- De Y só se volta pela aresta de M, nunca por aresta fora de M. Se o vértice de Y é livre, o caminho termina ali.
- P é só o ramo da raiz até o livre, não a árvore toda.
- M Δ P mantém as arestas de M que não estão em P (e as de M que estão em P saem; no Ex. 4 eram duas, não uma).
- A ordem das raízes segue o enunciado, mesmo que o quadro tenha seguido outra.
- Escrever "vértice livre/coberto" (de vértices), "aresta fora de M" (de arestas).
- Diferença simétrica (Δ) não é intersecção.
- Hall compara um subconjunto S com N(S), não "o lado X inteiro é maior que o lado Y".
- Não afirme "5 alocados" antes de construir M′; a aresta nova só torna a alocação completa possível.
- Vértices que a busca não visitou porque parou ao achar um livre não são "inalcançáveis"; inalcançáveis são os que ficam de fora de uma árvore fechada.

---

## 2. Fluxos em Redes — (a preencher)
## 3. Grafos Eulerianos e Carteiro Chinês — (a preencher)
## 4. Caixeiro Viajante — (a preencher)
## 5. Coloração de Grafos — (a preencher)
