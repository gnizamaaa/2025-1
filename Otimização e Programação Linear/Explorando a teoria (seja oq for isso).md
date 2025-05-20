Função objetivo a ser maximizada/miniminizada: $$c_1x_1 +c_2x_2 + c_3x_3$$
S.A(??)
$$a_{11}x_1 + a_{12}x_2 + a_{13}x_3  +s_1 =  b_1$$
$$a_{21}x_1 + a_{22}x_2 + a_{23}x_3 +s_2 = b_2$$
$$a_{31}x_1 + a_{32}x_2 + a_{33}x_3 +s_3 = b_3$$
s_1 -> Folga na primeira restrição
Tem como modelar sem ela fazendo$$a_{11}x_1 + a_{12}x_2 + a_{13}x_3 \le b_1$$Se existe uma solução para o problema linear, existirá uma solução em um vértice dos planos
$x_i, s_i \ge 0$ 

X são as produções, o que consome B, os recursos.
## As soluções
A solução básica baseada apenas nas variáveis de folga seria
$$\begin{align}
x_1,x_2,x_3 &= 0 \\
s_1 &=b_1\\
s_2 &=b_2\\
s_3&=b_3
\end{align}$$
Existe também a básica baseada na álgebra linear de x1 x2 x3 apenas
$X = A^{-1} B$
Resultando em 
$$s_1,s_2,s_3=0$$

E aí surge também a solução básica [x1,x2,s2]
![[Pasted image 20250520094621.png]]

Teremos $C_6^3$ soluções básicas, sendo algumas infactíveis e outras apenas ruins quanto a função objetivo
É como se tivesse x1,x2,x3 definindo 3 planos de cortes. E que você quer buscar o máximo que ainda respeite o corte

s1,s2,s3 -> Não irá consumir nenhum recuso
## Simplex // Primal simplex
Simplex pega uma delas e caminha para aumentar o valor dela enquanto mantém os s das outras, até que pare em uma restrição específica (não necessariamente a mais permissiva)
Ele vai navegando as soluções básicas possíveis
![[Pasted image 20250520100814.png]]

## Soluções
Além disso há a divisão de soluções factíveis e infactíveis (quando um dos valores de X_i ou S_i tem valor negativo)

E há o grupo de soluções ótimas (Sendo o importante ser uma ótima factível)

As soluções infactíveis se dividem em dois grupos:
	Superótima -> Estão acima da solução ótima
		É a solução maravilhosa, altíssimo desempenho mas impossível
	Subótimas -> Estão abaixo da solução ótima


# Como avaliar quanto a otimalidade?

Devemos pensar sobre os Cs
Função objetivo a ser maximizada/miniminizada: $$C_1X_1 +C_2X_2 + C_3X_3$$
S.A $$Ax \le b \ \ \ x \ge 0$$
Isso pode ser visto como
$$C_1X_1 +C_2X_2 + C_3X_3 +0s$$
S.A $$Ax+Is \le b \ \ \ x \ge 0$$

$$\pi = C^I B^{-1}$$B->Conjunto das variáveis básicas colocadas uma ao lado da outra
	$B=A^I$
$$Ĉ^I = C^I - \pi A^I = 0$$
A ideia é fazer o custo relativo das variáveis básicas NULO
"custo relativo das variáveis básicas é NULO"

Só vou permitir mudar as variáveis não básicas
$$Ĉ^J = C^J - \pi A^J  \gt0 (maximizar); \lt0 (minimizar)$$
pode ser diferente de zero

Esse J é uma variável como $X_1$no nosso caso anterior

$\pi$-> Variável dual (variáveis duais)
	É o valor do recurso

$$C^{básicas}* X^{*} S^{*} = \pi *b$$


O $\pi$ ótimo $\pi^{*}$ é fixado para a solução ótima
O máximo valor de aluguel que o cara consegue achar

Eu sei que não é ótimo quando tenho uma variável não básica que caminhando o, é possível melhorar o pi, tem o Ĉ maior que 0 (para maximizar), Ĉ menor que 0 (para minimizar)

[Dualidade e sensibilidade Goldbarg] - Cap 4

Tabela de primal dual, buscar entender
Aparentemente pega a restrição e vai ver ela transposta, invertida
Forma padrão e canônica
Ambos encontram a solução ótima
Analisar as situações de viabilidade dos problemas primal x dual
u do Goldbarg é o $\pi$ nosso

O dual do dual é o primal