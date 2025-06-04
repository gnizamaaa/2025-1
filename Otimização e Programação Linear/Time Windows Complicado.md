# Time Windows Complicado
Como você consegue modelar tempos diferentes de percurso em um grafo?
	Você passar numa rua as 4h da manhã furando sinal é diferente de passar as 5h da tarde com todo mundo buscando filho na escola

Considerando que temos 3 horários, 3 tempos de percurso diferentes
Isso complica o modelo porquê ao invés de ter 10 arcos, terá 30 arcos e uma variável inteira que determina se está de manhã/tarde/noite e consequentemente quais arestas estarão disponíveis

Precisa levar em consideração o tempo de transitar, ou seja, mesmo saindo de manhã, se no meio do percurso ficar a tarde teria que mudar o custo.

K - Quantidade de caixeiros

Pode usar outras formas de complicar o problema com pickup & delivery e montagem de carga

Fazer um dos do benchmarks
https://lopez-ibanez.eu/tsptw-instances

Ver até onde o Gurobi aguenta, começar com um pequeno e depois tentar com grandes e os maiores são desafios mesmo

É interessante fazer um conversor do formato usado ali no benchmark para um json, apesar de mais prolixo fica muito melhor a apresentação

É tbm interessante fazer em inglês

Ver como transforma shapefile em grafo para fazer a segunda parte do trabalho
Entregar um trabalho como o mais comercial possível
Também é bem interessante a API do Google Maps, até para fazer um route para fazer uma matriz 10x10 por n horários por exemplo
# Graphical TSP
Só precisa passar por alguns nós, não todos, e possui um grafo grande

