Usou o slide AULA 10 - Branch and Bound USP  [[aula10.pdf]]

Upper bound, escolher pelo maior valor é uma das estratégias
Outra pode ser escolher a menor distância entre upper e lower bound
	Para quando é o foco achar rápido uma solução
A melhor solução factível até aquele momento é a solução incumbente

Constraint Programming
Buscar um algoritmo que apenas busque uma solução, não necessariamente a melhor.
	Mas sempre uma solução factível, que satisfaz as restrições
	Tendo as soluções você pode fazer eliminação por qualidade, podendo eliminar branchs que são piores por exemplo. Ou explorar aquele branch com isso


> Gurobi tem pronto o branch and bound inclusive com cutting plane

Branch and bound TSP -> https://www.sciencedirect.com/science/article/pii/S0167637720300171 
	Bom para ver coisas como Ifood
Tem como fazer um caixeiro viajante das peças de um carro para contornar as tarifas por exemplo (cadeias de suprimento muito elaboradas, industria avançada)
	Que a ordem importa até certo ponto, certas peças tem que vir antes de outras

Ola, pessoal

na aula de hoje veremos o algoritmo de Branch and Bound...

Slides (da USP): [https://sites.icmc.usp.br/andretta/ensino/aulas/sme0510-2-19/aula10.pdf](https://sites.icmc.usp.br/andretta/ensino/aulas/sme0510-2-19/aula10.pdf) 

Capítulo de livro interessante (com exercícios): [https://web.tecnico.ulisboa.pt/mcasquilho/compute/_linpro/TaylorB_module_c.pdf](https://web.tecnico.ulisboa.pt/mcasquilho/compute/_linpro/TaylorB_module_c.pdf) 

Complementado por alguns artigos interessantes: 

Este primeiro é muito "ensinador"... didático e profundo o suficiente para o nível de graduação em Ciência da Computação...

CLAUSEN, Jens. Branch and bound algorithms-principles and examples. **Department of computer science, University of Copenhagen**, p. 1-30, 1999.

[https://www.imada.sdu.dk/u/jbj/heuristikker/TSPtext.pdf](https://www.imada.sdu.dk/u/jbj/heuristikker/TSPtext.pdf) 

Estes dois a seguir segundo é para o nível de pós-graduação... recentes e modernosos...

MORRISON, David R. et al. Branch-and-bound algorithms: A survey of recent advances in searching, branching, and pruning. **Discrete Optimization**, v. 19, p. 79-102, 2016.

[https://www.sciencedirect.com/science/article/am/pii/S1572528616000062](https://www.sciencedirect.com/science/article/am/pii/S1572528616000062) 

Este segundo, então... descreve como se utilizar deep-learning para aprender qual a melhor forma de acelerar o B&B:

HUANG, Meng-Yu et al. MILP acceleration: A survey from perspectives of simplex Initialization and learning-based branch and bound. **Journal of the operations research society of china**, v. 13, n. 1, p. 1-55, 2025.

[https://shorturl.at/GBbGK](https://shorturl.at/GBbGK) 

 TOMAZELLA, Caio Paziani; NAGANO, Marcelo Seido. A comprehensive review of Branch-and-Bound algorithms: Guidelines and directions for further research on the flowshop scheduling problem. **Expert Systems with Applications**, v. 158, p. 113556, 2020. 

[https://shorturl.at/IBQhF](https://shorturl.at/IBQhF)


