Relembrou mínimos médios quadrados e adaptou para TLS (Total Least Squares) para ajustar uma reta a um conjunto de pontos
Lembrou um pouco de rede neural, em que se busca os pesos ótimos
A palavra principal eh **otimização**
Nasceu da engenharia de produção a matéria
GOLDBARG -> Livro bom para as duas primeiras
## Problemas que iremos explorar (aparentemente)
TSP (caixeiro viajante) pode ser modelado como Branch & Bound de diversas formas, iremos abordar
Carteiro Chinês -> Igual o Caixeiro viajante mas que os clientes são as casas ao longo da via (cada aresta em uma quantidade de clientes) e sempre tem que passar em todas arestas que tem cliente. (o original tem que passar em todas arestas, o que também significa passar em todos vértices, mas podendo visitar várias vezes o mesmo vértice)
	Uma aplicação clássica é a coleta de lixo, que é uma variação de n-carteiro chines, por ter mais de um carteiro, mais de um coletor de lixo
	Dá p reduzir o carteiro clássico a TSP, mas nem todas variações
Quando o problema fica muito grande, acaba tendo que usar heurística ao invés de Branch & Bound
Cutting-stock multi-período -> Cortar x barras em y tamanhos diferentes, com uma quantidade diferente para cada. Minimizando o desperdício (restos grandes), não necessariamente usar a barra até o máximo (sobrar só um restinho muito pequeno) porquê pode fica difícil utilizar aquele restinho
	Podemos dificultar o tornando bidimensional utilizando corte guilhotinado (que corta a peça uma reta inteira, sem cortar metade da chapa)
Empacotamento -> Tem que carregar o máximo de coisas (de tamanhos diferentes) utilizando uma mochila, sabendo que a mochila tem limitações de tamanho ou peso.
	Podem ter limitações múltiplas como pacotes que não podem ser carregados juntos, ou colocar mais de uma dimensão (peso E volume)
	Ele é muito parecido com o de corte
## Algoritmos a serem aprendidos:
- Simplex
	- Programação linear
	- Simplex canalizado (limitados por um limite inferior e superior)
- Branch and Bound
	- Problemas de programação inteira (igual ao linear mas só em inteiros), ou mistas (com algumas reais e outras inteiras)
- "Lagrangianas"
	- Gradiente descendente
	- SGD (stochastic gradient descent) [não linear]
	- Algoritmo de Newton
	- Não serão cobradas em trabalho, mas caso tenha algum interesse específico, pode escolher fazer trabalho com ela

## Linguagens de modelagem de otimização
- Cnvxpy - Bom para simplex, algumas Lagrangianas/gradiente/sgd/newton (quando as restrições são convexas)
	- Trabalhos não serão feitos sobre isso via de regra, a não ser que tenha alguém interessado especificamente em fazer algo com lagrangianas
- AMPL-Gurobipy - Bom para simplex, Branch and Bound (gera uma árvore de busca grande)
	- VAMOS USAR ESSA

# Simplex (começo da explicação)
Toda situação ótima está no politopo (ponto em que o plano objetivo sai do volume das soluções factíveis, da região factível. E sempre estará em um vértice.

Pense em uma hiper formiga, irá sair de um um ponto 0 na região factível,= e vai caminhar em uma aresta desde que a aresta faça aumentar a função objetivo, chegou em um vértice, você para e pergunta "essa solução é ótima?", ou seja, não tem aresta saindo desse vértice que melhore a solução, caso seja ótima, ok, caso contrário, segue a aresta boa.

Sempre caminha por uma aresta!
