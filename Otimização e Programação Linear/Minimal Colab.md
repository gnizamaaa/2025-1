# Shadow Price
https://colab.research.google.com/drive/1xo3RnoD7AVD84-gDC6h58qc0UrCNymei
Shadow Price - Preço soma?
Como a usina de baixo custo se relaciona com as outras?
COmo que as outras variáveis vão diminuir se aumentar essa
$$\pi = C^B [A^B]^{-1}$$
Serve para decidir onde vale a pena investir para aumentar a capacidade
Para X não nulo, é possível usar:
$$\pi b = X^B$$ 

# Fluxo máximo
https://colab.research.google.com/github/ampl/colab.ampl.com/blob/master/authors/gomfy/ampl-lecture/network.ipynb

Tem como resolver o problema de corte mínimo//fluxo máximo utilizando simplex
Se cria um arco externo (conectando as extremidades), em que cada nó temos uma quantidade de fluxo máximo (sempre mantendo o fluxo de entrada = fluxo de saída) e arestas como restrição
Inicia com 1 e vai maximizando
Uma variável estar na base, significa que o valor está entre o fluxo 0 e fluxo máximo da aresta, nas outras ou estará em 0 ou na capacidade máxima, o nó fica na árvore até que atinge o seu limite superior, e aí sai da base.
As não básicas tem que estar ou no limite inferior ou no superior
Não básica a gente muda uma de cada vez, as básicas iremos passar de uma aresta para outra.

A base sempre será uma árvore dentro do nosso grafo

Devemos maximizar: $$\sum{start}_$$
Nossa restrição será:
$$\sum{f_{ij}} - \sum{f_{jk}} = 0  \ \ \ \ \  \forall i$$


# Origens e destinos
https://colab.research.google.com/github/ampl/colab.ampl.com/blob/master/ampl-lecture/steel_lecture.ipynb

Você quer minimizar o custo de transporte, cada origem tem capacidade de produção e cada destino sua demanda
Soma das prod. nas origens== Soma dos consumos dos destinos

Um fator complicador seria adicionar vários produtos, incluindo manutenção das máquinas, limpeza, limpeza entre produtos.
	Dependendo vai valer a pena trazer um produto específico de outro lugar e não produzir no lugar próximo do destino
