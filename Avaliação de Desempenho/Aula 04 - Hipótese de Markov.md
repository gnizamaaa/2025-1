> O futuro só depende do presente, **independe** do passado

A distribuição exponencial é uma boa e conveniente aproximação para diversas aplicações. A pergunta é se tem como fazer uma solução markoviana para o problema, se tem como obter uma solução boa com uma janela de tempo viável.
Assim você poupa de "carregar a bagagem para frente"

Nós terminamos a última aula mostrando que a distribuição exponencial é Markoviana (sem memória).

# Exercício:
Rhuan chegou a uma agência dos correios. 
A agência possui dois caixas. Quando Rhuan chegou à agência o primeiro caixa estava atendendo o Igor, o segundo caixa estava atendendo o Bruno.
O tempo de serviço é exponencialmente distribuído com razão $\mu$.

## Qual é a probabilidade de que Rhuan seja o último a sair da agência?

O Igor pode sair, eu (Rhuan) entrar e sair antes do Bruno.

Igor estava a 1:30h (90min), Bruno a 10min
	Não importa, porquê "ninguém tem passado", não tem memória

Para Rhuan sair antes, um dos dois precisa acabar, eu entrar para ser atendido e eu terminar o atendimento antes
	Dada a situação de que eu entrei, estou em pé de igualdade com o que estava a mais tempo, se torna 50%
	E um dos dois da fila precisa terminar antes do outro (é uma certeza), logo é 50%

**Resultado:** A probabilidade de eu, Rhuan, ser o último a sair é 50%

## Dado que chegou uma outra pessoa na fila, qual é a possibilidade de eu ser o último a sair?

Tenho 50% de chance de sair depois da outra pessoa que está sendo atendida.
Quando estiver em uma em uma situação com a ultima pessoa da fila, tenho 50% de chance de sair mais rápido que essa pessoa.

Considerando que precisa acontecer o evento A E o evento B, temos que:$$Pr\{A\}*Pr\{B\} -> 0.5*-0.5 -> 0.25$$
## Dada a circunstancia inicial de Igor, Bruno e Rhuan
A chance de Rhuan ser o primeiro a sair é 0% (alguém precisa ser atendido antes para liberar o caixa), a chance de ser o segundo é 50%, e a chance de ser o terceiro a ser atendido é 50%.

# Teorema
Dado que $X_1 \sim Exp(\mu_1),\ X_2\sim Exp(\mu_2)\ e \ X_1 \perp X_2$ 
$$Pr\{X_1 \lt X_2\} = \dfrac{\mu_1}{\mu_1+\mu_2}$$
A probabilidade de X1 ser menor, ocorrer antes, de X2
X1 ser paralelo a X2 é o fato de que um não altera nada em outro. Saber que um ocorreu não afeta o espaço amostral da outra em nada
## Exercício
Considere um sistema computacional formado por uma CPU e um disco. O tempo de vida da CPU é exponencialmente distribuído com média de 500 horas e o tempo de vida do disco é distribuído exponencialmente com média de 100 horas.
Qual é  a probabilidade de que uma falha, quando esta ocorrer, tenha sido causada pela CPU?
> *Obs: Aqui tempo de vida na verdade é MTBF (Mean Time Between Failures)* 

$X_1$ é o tempo de vida da CPU
$X_2$ é o tempo de vida do disco
Ocorreu uma falha, qual é a probabilidade dessa falha ter sido de CPU? Qual é a probabilidade de $X_1 \lt X_2$?

A média é o inverso da razão! Tome cuidado com isso $\lambda$ ou $\mu$ nesse caso, será $1/500$ 

$$Pr\{X_1\lt X_2\} = \dfrac{\dfrac{1}{500}}{\dfrac{1}{500}+\dfrac{1}{100}} = \dfrac{\dfrac{1}{500}}{\dfrac{6}{500}} = \dfrac{1}{6}$$
# Teorema
Dado que $X_1 \sim Exp(\mu_1)$,  $X_2 \sim Exp(\mu_2)$ e  $X_1 \perp X2$.
Assuma que $X = min(X_1,X_2)$
Então $$X\sim Exp(\mu_1 + \mu_2)$$
Um bom exemplo são dois componentes em série, o que falhar primeiro carrega o sistema, logo o sistema falhará com o mínimo
	É um OU, por isso a soma *(lembre que é a soma de RAZÕES e não de médias, por isso faz sentido)*
## Prova:
$$Pr\{X\gt T\} = Pr\{min(X_1,X_2) \gt T \} \to Pr\{X_1\gt T\ \wedge \ X_2\gt T \}$$
![[Pasted image 20250514103301.png]]
X1 E, and, X2 tem que ser maior ~~igual~~ que T

Lembrando que X=T não faz diferença, porquê a probabilidade em um ponto é 0. É a mesma coisa que: $Pr\{X\ge T\} = Pr\{min(X_1,X_2) \ge T \} \to Pr\{X_1\ge T\ \wedge \ X_2\ge T \}\ (Pr\{A\cap B\})$

Como são independentes $X_1 \perp X2$, a probabilidade da intersecção é meramente o produto das probabilidades
$$Pr\{X_1\ge T\} * Pr\{\ X_2\ge T \}\ (Pr\{A\}*Pr\{B\})$$
Isso é $$e^{-\mu_1 t}*e^{-\mu_2 t} \to e^{-(\mu_1+\mu_2)t}$$Logo ela é uma probabilidade exponencialmente distribuída com razão $\mu_1 +\mu_2$. $X\sim Exp(\mu_1+\mu_2)$

