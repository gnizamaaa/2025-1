Imagine uma laminadora que pode produzir chapas ou bobinas de aço, em que as bobinas são mais lentas de serem produzidas, valem mais por tonelada e cada uma tem uma certa demanda (quanto que os clientes estão dispostos a comprar)
Sabendo que você tem apenas 40 horas de produção, quantas bobinas e quantas chapas devo produzir para maximizar o lucro?

Conseguimos definir as constrains, as limitações de forma visual com o gráfico abaixo, onde a cinza é a região factível
![[Pasted image 20250424095015.png]]
E conseguimos definir o lucro com os 
![[Pasted image 20250424095024.png]]

E então conseguimos encontrar o lucro máximo factível, sobrepondo um ao outro
![[Pasted image 20250424095444.png]]

Se eu tenho um problema que tem solução ótima, então existe uma solução ótima que está em um vértice da região factível
	Super-ótima -> Sol. melhor que a ótima, que está fora da região ótima

E podemos codar esse problema no AMPL, e chamar o solver (nesse caso minos), para encontrar a solução ótima
![[Pasted image 20250424095657.png]]

Como dito anteriormente na [[Otimização e Programação Linear/Introdutória|Introdutória]], comece em um vértice, avalie se há alguma direção que melhora a função objetivo, escolhe (qualquer uma) das que melhora a função e explora.
Obs: Simplex funciona bem para n-dimensões

Tem como fazer simplex distribuído também, em que se explora os pontos com dois computadores que de tempos em tempos trocam mensagem para saber o progresso, com cada um explorando uma direção. Mas não é muito bom

Primal -> trabalha com solução subótimas mas factíveis
Dual -> trabalha com soluções superótimas mas infactíveis
	Mantém a otimilidade e buscando a factibilidade, cada vez é uma solução mais factível
Primal-Dual -> Começa em uma solução nem ótima nem factível
	Vai dançando forró, um passo para a ótima, outra para factibilidade
## O que é necessário definir no modelo
- sets, like the products
- parameters, like the production and profit rates
- variables, whose values the solver is to determine
- an objective, to be maximized or minimized
- constraints that the solution must satisfy

De forma algébrica, o mesmo problema fica assim:
![[Pasted image 20250424101350.png]]
No AMPL podemos escrever o modelo como
![[Pasted image 20250424101521.png]]

E para definir a instância, os dados base, se cria um arquivo com a seguinte sintaxe. O problema fica separado dos dados
![[Pasted image 20250424101647.png]]

Também não é necessário fazer isso em texto, podemos usar XML principalmente JSON (mais organizado de ler) e PANDAS DATAFRAME!!!



