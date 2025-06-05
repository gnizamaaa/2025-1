Livro do GoldBarg

Está relacionado a problemas como
- DIO -> Fibra ótica
- IP/SDH -> Roteamento **de circuito**
- WDM -> Frequências múltiplas na mesma fibra, que podem ser separadas, juntadas alguns pontos

Todos esses problemas você vai ter terminais e pontos podendo ter pontos terminais.
Procurar uma árvore que nutre todo mundo de forma mais barata possível

Exemplo utilizando WDM, SDH e DIO na prática
![[Pasted image 20250605102506.png]]
Essas redes fazem multiplexação por comprimento de onda
Surgem alguns problemas como otimizar essa rede de topologia anel
https://www.submarinecablemap.com/

## PEG (Steiner Generalizado)
Procurar um grafo, mais barato possível, que mantém a conexão mesmo após a perda de k conexões (se torna uma árvore após k conexões)

Minimizando o custo de montar a rede
- A primeira restrição -> cada par origem destino, verifica qual é o par origem destino que vai fazer conexão através daquele arco e tem a maior demanda de conexão somado a passagem de i para j e de j para i.
	Vê qual arco tem o maior fluxo, considerando as duas direções (para determinar se instala ou não o arco), se term fluxo deve ser instalado (ter valor maior que 0)
- Segunda -> A soma dos fluxo de todos os arcos saindo de k deve ser
	Quantos y eu vou colocar saindo de cada k
- Terceira -> Mesma coisa nos destinos
- Quarta -> Faz a garantia que a conexão nos nós de passagem também saem do nó de passagem
- Quinta -> X_{i,j} ou são 0 ou 1
- Sexta -> Valores de y_{i,j} são maiores que 0

## Off-topic +/-
O maior perigo para um eventual golpe de estado por exemplo, seria matar a rede tradicional de internet https://www.submarinecablemap.com/ 
	Se cortar os cabos de fortaleza simplesmente tira a rede do Brasil (de modo internacional)
E acabaria tendo que confiar em redes como a Starlink...

Isso poderia ser contornado com a otimização priorizando também a sobrevivencialidade da rede (quantos k é possível cortar antes de tenha perda da operação)

**Prox. Aula** -> Tutorial arvix karush khn tucker (KKT Conditions, First-Order and Second-Order Optimization, and Distributed Optimization: Tutorial and Survey )
https://arxiv.org/abs/2110.01858