Considere novamente a rede de fila mais simples que existe, a rede com um único servidor.
$\lambda$->||||||]($\mu$)->

Nesta rede nós sabemos, pela sua representação, que a razão média de chegada é $\lambda$, e a razão média de serviço $\mu$.
Nós queremos determinar várias métricas de desempenho, por exemplo qual é o tempo médio que um trabalho fica na fila.
Tal como está colocado nós simplesmente não conseguimos determinar o seu valor.

O que nós precisamos saber para responder a esta pergunta e outras semelhantes a respeito do desempenho do sistema? Quais são as distribuições probabilísticas do tempo de serviço e do tempo entre chegadas sucessivas?

Precisa saber como é a distribuição do tempo de serviço e de chegadas sucessivas para saber o tempo médio. *Se for chegar mais perto de constante, vai ter menos fila do que se tiver uma porrada chegando de uma vez* 

Tempo de serviço segue uma distribuição exponencial, é uma boa forma de se aproximar do mundo real enquanto é uma forma aceitável de se resolver o sistema

# Distribuição exponencial
Nós dizemos que uma variável aleatória X é distribuída exponencialmente com razão $\lambda$ $(X \sim Exp(\lambda))$ se X tem a seguinte função densidade de probabilidade: $$f(x) = \begin{cases}
\lambda e^{-\lambda x};\ se\ x\ge0;\\
0\ se\ x<0\\
\end{cases}$$
A função de distribuição acumulada, $F(x) = Pr\{X<=x\}$ é dada por
$$F(x) = \int_{-\infty}^{x}{f(y)dy} = \begin{cases} 1-e^{-\lambda x};\ x\ge0\\ 0;\ x<0\\\end{cases} = 1-e^{-\lambda x}$$
Se a variável aleatória é real, ela é **contínua**, pode obter qualquer um valor

Variável **discreta** -> pode só assumir alguns valores, como os inteiros, como um intervalo, conjunto, de inteiros.

Se a variável é contínua, a variável vai ter função densidade de probabilidade
Se for discreta vai ser massa de probabilidade

Vamos buscar a possibilidade de x ser menor igual a 20 $$F(x) = Pr\{X\leq20\} = \int_{-\infty}^{20}{f(y)dy}$$

E agora para $Pr\{X>20\}$? Basta fazer $$Pr\{X>20\} = 1- Pr\{X\leq20\} = 1- F(x) = 1 - (1-e^{- \lambda x}) = e^{-\lambda x}$$
Variável aleatória contínua não tem probabilidade no ponto, vai ser sempre 0. $Pr\{X=x\}$ vai ser sempre 0, isso porquê a integral vai ter limite inferior e superior igual.

Valor esperado da variável aleatória $X \sim Exp(\lambda)$ (valor médio)$$E[X] =\int^{\infty}_{-\infty}{xf(x)dx}$$
Vamos continuar o raciocínio
$$E[X] =\int^{\infty}_{-\infty}{xf(x)dx} = \int^{\infty}_{-\infty}{x\lambda e^{-\lambda x}dx} = 1/\lambda$$
**Onde tem somatório na discreta, tem integral na contínua**
## Para uma variável discreta (parenteses)
$$Pr\{X=10\} = 0.3$$$$Pr\{X=8\} = 0.2$$$$Pr\{X=6\} = 0.1$$$$Pr\{X=4\} = 0.3$$
$$Pr\{X=0\} = 0.1$$

Qual é a nota média? Qual é o valor esperado?$$E[X] = 10*0.3 + 8*0.2+6*0.1+4*0.3+0*0.1 = 6.4$$
**Onde tem somatório na discreta, tem integral na contínua** 

## Voltando a contínua
$$E[X] =\int^{\infty}_{-\infty}{xf(x)dx} = \int^{\infty}_{-\infty}{x\lambda e^{-\lambda x}dx} = 1/\lambda$$
O segundo momento é$$E[X^2] = \int^{\infty}_{-\infty}x^2f(x)dx = 2/{\lambda^2}$$
A variância será  $$Var(X) = E[X^2] - (E[X])^2 = \dfrac{2}{\lambda^2} - \dfrac{1}{\lambda^2}=\dfrac{1}{\lambda^2}$$
Desvio padrão vai ser igual a média $$\sigma(x) = \sqrt{Var(X)} = \dfrac{1}{\lambda}$$
## Exercício
Suponha que o tempo que um cliente fica em um banco é exponencialmente distribuído com média de 10 minutos.

**a) Qual é a probabilidade de o cliente ficar mais que 5 minutos no banco?**
Estamos buscando $$Pr\{X>5\} = e^{-5\lambda}$$
Para calcular isso, precisamos de lambda, que podemos obter com:
$$E[X] = 10min \to \lambda=1/10 $$

Então $$Pr\{X>5\} = e^{-5/10} = e^{-1/2}$$
**b) Qual é a probabilidade de que o cliente fique no banco mais do que 15 minutos? Dado que ele está no banco depois de 10 minutos?**
	Ou seja, eu tenho a certeza de que ele ficará 10min no banco, qual será a probabilidade de ele ficar, ao todo 15min?
Estamos buscando $Pr\{A|B\}$ $$Pr\{A|B\} = \dfrac{Pr\{A\cap B\}}{Pr\{B\}}$$
**Se fossem dois eventos independentes** -> $Pr\{A\cap B\} = Pr\{A\} * Pr\{B\}$ 

_*Sendo A $Pr\{X>15\}$ e B $Pr\{x>10\}$*_
No nosso caso, é diferente, já que para A $(Pr\{X>15\})$ ocorrer, B $(Pr\{x>10\})$ TEM QUE OCORRER.
	Para você esperar 15 minutos, você precisa esperar 10 minutos

Quem fica mais que 15 minutos, ficou mais que 10 minutos. A intersecção é quem ficou mais que 15 minutos
Logo, $$Pr\{A\cap B\} = Pr\{A\}$$
E então: $$Pr\{A|B\} = \dfrac{Pr\{A\}}{Pr\{B\}} \to \dfrac{e^{-15/10}}{e^{-10/10}} \to \dfrac{e^{-3/2}}{e^{-1}} \to e^{-1/2}$$
# Conclusão importantíssima 

**É IGUAL AO TEMPO DE FICAR 5 MINUTOS!!!!!!** 
É como se tivesse acabado de entrar no banco
	Vai ser sempre igual para distribuição exponencial
**Exponencial é sem memória**
É aquela pessoa viciada que sempre vai achando que na próxima vai dar certo
**É Markoviano, para o futuro o passado não interessa, só interessa o presente**
	Tudo o que foi e o que poderia ter sido converge para apenas uma coisa, o que é.
	Simplesmente esqueça o passado, só interessa o presente
Suposição de Markov é importantíssimo para computação

A realidade não é markoviana, mas aproximar para uma "realidade" markoviana fica muito mais simples, muito menos coisa a se levar em conta. Fica mais fácil de só se basear na realidade atual.
	Tratar como é na realidade é inviável.
	Podemos fazer um markoviano com janela de 2,3 dias para prever a previsão do tempo por exemplo. Quanto maior a janela, maior a complexidade no modelo mas provavelmente maior acurácia.

A distribuição normal por exemplo iria se comportar "tendo memória" por exemplo