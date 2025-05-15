Qual é a rede de custo mínimo apenas contando o custo de caminhar na rede
$$Min \sum_{i,j \in N}c_{ij}f_{ij}$$
S.A$$\sum_{i\in N}f_{ij} = \sum_{i\in N}f_{ij} +e_j$$ $j \in N$ $f_{ij}\ge 0$ 
$e_j$ sendo a saída do nó. Veja na imagem
![[Pasted image 20250515093643.png]]

# Agora considerando o custo de implementar um arco
Qual é a rede de custo mínimo contando o projeto, o custo de implementar o arco
M é a capacidade do arco, uma constante determinada em algum lugar
X_ij é uma variável de decisão que vai ser determinada pelo simplex//solver
C grande é o custo de implantar o arco

$$Min \sum_{i,j \in N}{c_{ij}f_{ij}} + \sum_{i,j \in N}{C_{ij}X_{ij}}$$
S.A$$\sum_{i\in N}f_{ij} = \sum_{i\in N}f_{ij} +e_j$$ $j \in N$ $f_{ij}\le M * X_{ij}0$ 



# Modelando o caixeiro viajante
Deixar uma carga, uma caixa em cada nó
O somatório dos fluxos saindo do primeiro nó deve ser igual a 7 (n-1)$$\sum_{k\in N}{f_{1k}} = 7$$
Tem que garantir que apenas um arco saia do primeiro nó $$\sum_{k\in N}{X_1k} = 1$$
A carga tem que chegar de volta (na origem) vazia$$\sum_{k \in N} f_{k1} = 0$$
Deve ter um caminho para a volta$$\sum_{k\in N} x_{k1}  = 1$$
Não deve poder dividir o fluxo (sair 2 caixeiros de uma vez), então precisa de uma restrição para isso. $$\sum_{k\in N}{x_{kj}} = \sum_{k\in N}{x_{jk}} \ \ \ \forall j \in N, j\ne 1$$
Tem um custo maior do que o da aula passada, isso porquê vai ter que percorrer a decision tree inteira

Até que veio a ideia de percorrer com "mais de uma caixinha", mais um caixeiro começando no mesmo lugar, mesma quantidade que precisa percorrer.
	Com uma "brincadeira" um roda para um lado e o outro roda para o outro. O vermelho vai andar no contra-fluxo do arco
	Onde carrega 7 azuis, carrega 0 vermelhos, onde ta 6 azuis, tem 1 vermelho
	A soma do azul e vermelho nas arestas usadas sempre vai ser 7 (n-1, sendo o 1 a origem)
Formulação multiproduto do TSP, similar a https://onlinelibrary.wiley.com/doi/full/10.1002/net.21521

Ai veio a ideia de aumentar mais ainda a quantidade de produtos.
Um produto para cada nó - saída. Ai cada produto tem um destino, tem uma cor para cada par de produto e nó. Cada um tomando um rumo mas que se soma o custo.
Aumenta muito a quantidade de variáveis, fica com N-vezes mais que a primeira formulação.
Mas não aumenta a quantidade de variáveis que vão ser determinadas pelo solver. Único custo passa a ser a RAM
Com a decomposição de Benders (arco-caminho), a solução fica mais rápida.

Tem como ter um caixeiro viajante (problema de roteamento) com restrição de janela de tempo, para modelar se adiciona um segundo custo, na verdade não se ignora o c pequeno. Coloca o tempo que demora para percorrer aquele arco. 
	Assim também tem como determinar o quanto demora para chegar em cada nó, já que, tendo um pacote para cada nó, basta saber o tempo, o custo, daquele pacote.

Tem como determinar com essa formulação de par pacote nó, também a ordem em que os nós são visitados.
	Basta determinar o fluxo de chegada, fluxo maior = visitado primeiro
	Pode criar uma restrição p determinar a ordem de chegada

Como modelar se cada caixeiro sai de um lugar diferente e todos nós ainda precisam ser atendidos. Precisamos tomar a decisão de qual caixeiro atende qual cidade, tem um problema de alocação.
	Um caixeiro não pode atender mais de z cidades, a distância entre elas não é problema porquê o custo C grande já resolve isso.
	As vezes vai ter mais de um caixeiro visitando uma cidade
	

> [!TRABALHO]
> Pega um artigo, ve um modelo, transforma em ampl, resolve no gurobi [Trabalho] 
> Fazer o mais próximo do real possível mas não precisa fazer uma ferramenta pronta para vender
> Geopandas



