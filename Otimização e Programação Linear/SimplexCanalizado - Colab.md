O que são variáveis de folga, artificiais e excesso [Voltar aqui]
Essa nota inteira está comprometida porquê não estou conseguindo acompanhar essa aula

Apenas com as variáveis de folga positivo conseguimos fazer uma matriz identidade
	Tem que fazer a manipulação $-2x > -5$ -> $2x < 5$

Para qualquer problema Ax {>=, = <=} b com variáveis de folga podemos fazer a manipulação abaixo para conseguir obter igualdades
	$>= -> -y_{excesso}$
	$<= -> +y_{folga}$ 
	$=   -> y_{artificial}$ 
Você pega a equação e inclui uma variável, torna ela uma igualdade
$5x_1 +3x_2 >= 5$ -> $5x_1 +3x_2 -e_1= 5$

Se tenho uma restrição do tipo $5x_1 +3x_2 <= -5$, é uma infactibilidade já que não há valores positivos que atendam.

As variáveis artificiais precisam ser tiradas da soluçãoPOA na minha mente eh mó caro 
	Minimiza a soma das variáveis artificiais, quando 0 bom!
	Consegue construir um problema de fase 1 após isso, retomando agora o problema original

Podem ter vaiáveis não básicas iguais a 0, as básicas $X^{-J}$ devem ser iguais a 0

E no simplex depois a gnt aumenta a não básica aumentar, crescendo até o limite


1. Partindo de uma sol inicial base factível, pega uma não básica coloca na base e faz aumentar
2. Calcula os custos relativos para as variáveis não básicas zeradas 
	custo relativo = custo original - custo relativos das variáveis básicas multiplicadas pela inversa da base multiplicada pela coluna da variável que ta entrando
3.  Verificar a otimalidade
4. Selecionar a variável entrante, que possui o custo que me interessa
5. Calcula o que isso faz com a solução
6. Determina a variável sante (faz o teste da razão mínima)
7. Atualiza a base
8. Faz pivoteamento
9. Repete

# Agora o nó (canalização)
Agora todas as variáveis vão ser limitadas por um limite superior e inferior, com isso vai surgir um problema como
Ax =b
L <= x <= U

Uma hora uma do teto bate no chão ou a do chão bate no teto ou chão

Vão ser grupos de variáveis de limite inferior e superior
$Z_X_L ^L + B_X_B + A_X_U ^U = b$

As básicas vão poder ter qualquer valor desde que respeitem a equação
$X_B = B^{-1} (b-A_X_L ^L -A_X_U ^U)$