Dualidade.ipynb
Solução básica 55 -> Ótima e factível
Poderia ter duas ou mais soluções ótimas e qualquer combinação linear entre elas que fossem factíveis seriam também ótimas. Assim tem como formar arestas, planos ótimos.

# Teorema das folgas complementares
Dado um par de programas duais, uma condição necessária e suficiente para que as soluções x⁻ e ⁻u sejam ótimas é que se verifiquem as seguintes relações de complementaridade de folga:
$$ \begin{align}
u(Ax-b)=0\\
(c-\pi A)x =0
\end{align}$$
Uma solução básica de um problema é a mesma solução básica no problema dual (pode ser mapeado 1 para 1)
Uma solução factível no primal vai ser uma solução ótima ou super-ótima no dual

Quando se coloca uma nova restrição Primal simplex para super ótimas infactíveis)
A não básica que alcançar 0 primeiro entra para o conjunto enquanto expulsa uma básica
Se nenhuma alcançar 0, o problema se torna ilimitado. 
e vai buscando a factibilidade do primal

Necessariamente se ela atende as duas folgas, vai ser ótima e factível

Vamos estar lendo o Goldbard
Infactível sub-ótima não serve nem para o primal simplex nem para o dual simplex, apenas para o primal-dual (que não estudamos)

## Interpretação econômica
Uma restrição está no talo tem um b do lado direito

O valor da unidade marginal de um fator de produção é igual ao máximo valor da produção que poderia ser obtida usando essa unidade do fator.

Qual é o valor marginal de um caixa a mais no supermercado? Que tá apertado é que tem o maior valor

Vai ver o custo marginal dos b's e associar a u

Olhar o exemplo do Goldbard
Os dois, primal e dual, são analisados em conjunto.


Branch-and-bound o próximo capítulo
	Como posso conseguir a maior solução inteira com base na relaxada, qual é a variável que deve ser apertada? Qual dos sub-problemas vou atacar, onde vou fazer branch
	Ele faz como se pudesse atravessar as paredes, mas depois adiciona as restrições
