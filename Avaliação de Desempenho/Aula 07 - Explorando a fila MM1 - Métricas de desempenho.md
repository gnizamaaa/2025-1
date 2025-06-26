As probabilidades só convergem para valores quando o que sai em casa estado é igual o que entra
Se tiver saindo mais que entrando no estado, a probabilidade tá diminuindo
Se tiver entrando mais que saindo, a probabilidade tá aumentando

## Pergunta
Quais condições devem ser satisfeitas para que as probabilidades dos estados tenham convergido para determinados valores
$\pi_i$ = probabilidade do sistema estar no estado i

Ele imaginou igual Kirchhoff, o que entra é igual o que sai e fez um corte ao redor do estado (incluindo o auto laço como dentro)
	Assim o auto laço fica "inútil", não precisa considerar

Agora podemos fazer a equação de equilíbrio daquele estado
Ex. para o estado 0:
0: $\lambda \delta * [prob\ de\ estar\ no\ estado\ zero]$ -> O que sai
$\mu \delta \pi_1$ -> O que entra
Simplificando:$$\lambda\pi_0=\mu\pi_1 $$
Logo:$$\pi_1=\dfrac{\lambda}{\mu}\pi_0$$

E o diagrama pode ser extremamente simplificado, sem os autolaços e cortando os delta

Para o estado 1:
$$\lambda \pi_1 +\mu\pi_1 = \lambda \pi_0 + \mu \pi_2$$
Considerando a equação de equilíbrio do estado anterior:$$\lambda \pi_1 = \mu \pi_2 \equiv \pi_2=\dfrac{\lambda}{\mu}\pi_1 \equiv \pi_2=(\dfrac{\lambda}{\mu})^2 \pi_0$$

Sempre tem como ir obtendo o próximo estado, isso se repete, veja obtendo o terceiro pi
$$\lambda\pi_2+\mu\pi_2 = \lambda\pi_1+\mu\pi_3 \equiv \pi_3=\dfrac{\lambda}{\mu}\pi_2 \equiv \pi_3 = (\dfrac{\lambda}{\mu})³\pi_0$$

Podemos enfim inferir a probabilidade do sistema estar no estado i
$$\pi_n=(\dfrac{\lambda}{\mu})^n \pi_0$$
Definindo rho como $\rho =(\lambda /\mu)$ 

$$\pi_n = \rho^n \pi_0$$

Não estamos utilizando o fato de que o sistema TEM que estar um certo estado$$\sum^{\infty}_{n=0}\pi_n = 1 $$
Isso é $$\sum^{\infty}_{n=0}\rho^n\pi_0 = 1 \to \pi_0 \sum^{\infty}_{n=0}\rho^n =1 \to \pi_0 = \dfrac{1}{\sum^{\infty}_{n=0}\rho^n}$$

Sabendo que $\lambda$ precisa ser maior que \mu para cumprir a estabilidade do sistema, da fila ser finita
Assim $\rho$ será menor que 1 sempre e a PG formada por $\sum^{\infty}_{n=0}\rho^n$ irá convergir para $\dfrac{1}{1-\rho}$
E podemos então dizer que $$\pi_0 = 1-\rho$$ e então que:$$ \pi_n = \rho^n (1-p)$$

## Exemplo
$\lambda$ = 3 alunos/min $\mu$= 5 alunos/min 
$\rho$ =0.6
Então podemos calcular a probabilidade de qualquer estado, por exemplo 10 alunos no RU
$$\pi_{10} = (0.6)^{10} (1-0.6) = 0.0024$$

### Descobrindo quantos trabalhos estarão no sistema
E agora para saber $E[N_s]$ ? O valor esperado da variável aleatória do número de trabalhos no sistema? Qual o número médio de trabalhos no sistema?

Como calcula o valor esperado de uma variável aleatória discreta? $$E[N_s] = \sum^{\infty}_{n=0}n\pi_n$$
Podemos então seguir$$E[N_s] = \sum^{\infty}_{n=0}n \rho^n\pi_0 \to E[N_s] = \pi_0 \sum^{\infty}_{n=0}n \rho^n$$
E lembrando que $\rho \dfrac{d \rho^n}{d\rho}=n \rho^n$, então:$$E[N_s] = \pi_0 \rho\sum^{\infty}_{n=0} \dfrac{d \rho^n}{d\rho}$$
Soma de derivadas é derivada da soma!!! $$E[N_s] = \pi_0 \rho \dfrac{d( \sum^{\infty}_{n=0}\rho^n)}{d\rho}$$
Lembrando de pi_0! $$E[N_s] = \pi_0 \rho \dfrac{d(\dfrac{1}{1-\rho})}{d\rho} = \pi_0 \rho\dfrac{1}{(1-\rho)^2} \to (1-\rho) \rho\dfrac{1}{(1-\rho)^2}$$(fez esse passo utilizando $\dfrac{d(1-p)^{-1}}{d\rho} = -1 (1-\rho)^{-2}(-1)=\dfrac{1}{(1-\rho)^2}$) 

Logo $$E[N_s] = \dfrac{\rho} {(1-p)}$$
### Descobrindo quanto tempo se passa no sistema
$E[T_s]$ É quanto tempo se passa no sistema, tempo médio no sistema
**Não é de serviço é de sistema!!**
É uma variável contínua, não discreta


> [!Relembrando]
> Uma das coisas mais importantes, relembrando: A lei de Little que serve para qualquer sistema ergótico (Um sistema em que indivíduos, clientes, não desaparecem, não podem ficar infinitamente no sistema ou saírem por nada. Também não pode ser criado um cliente dentro do servidor. Cliente n pode ser criado ou deletado no sistema)  $$E[N_s] = \lambda E[T_s]$$
> Para lembrar da lei, quem precisava de mais espaço no restaurante? FastFood ou SlowFood?


E $E[N_s]$ nós temos!
$$\dfrac{\rho}{(1-p)} = \lambda E[T_s]$$
Passa $\lambda$ dividindo
$$E[T_s] = \dfrac{\dfrac{1}{\mu}}{(1-p)}$$
E podemos simplificar como:
$$E[T_s] = \dfrac{\dfrac{1}{\mu}}{(1-p)} = \dfrac{\dfrac{1}{\mu}}{(1-\dfrac{\lambda}\mu)} = \dfrac{\dfrac{1}{\mu}}{(\dfrac{\mu -\lambda}\mu)} = \dfrac{1}{\mu-\lambda}$$
$$E[T_s]= \dfrac{1}{\mu-\lambda}$$
### Tempo na fila
E Agora podemos saber o tempo na fila também!
$$E[T_q]= E[T_s]-E[S]$$
Sendo $E[S]$ o tempo de serviço, o tempo que o servidor demora para executar o seu serviço
$$E[T_q]= \dfrac{1}{\mu-\lambda}-\dfrac{1}{\mu}$$
## Exemplo
$\mu$ = 20/min, $\lambda$ = 10/minuto

$$E[T_s] = \dfrac{1}{20-10} = \dfrac{1}{10} min = 6seg$$
$$E[T_q] = \dfrac{1}{10}- \dfrac{1}{20} = 0.1-0.05 = 0.05 min = 3seg$$
Segundo

$\mu$ = 20/min, $\lambda$ = 19/minuto

$$E[T_s] = \dfrac{1}{20-19} = 1min$$
$$E[T_q] = \dfrac{1}{19}- \dfrac{1}{20} = 1-0.05 = 0.95 min = 57seg$$


A medida que $\rho$ vai se aproximando de 100%, $\lambda$ de aproximar de $\mu$; $E[T_q]$ se aproxima de forma não linear, quase exponencial para infinito.
	Mais saturado fica o sistema

### Número médio de trabalhos na fila
Agora qual é o número médio de trabalhos na fila? $E[N_q]$ 
	Uma variável aleatória discreta $E[N_q] = \sum^{\infty}_{n=1}(n-1)\pi_n$ -> Se tenho um trabalho no sistema tenho nenhum na fila, se tenho 2 tenho 1 na fila... 
Podemos já substituir $\pi_n$, $$E[N_q] = \sum^{\infty}_{n=1}(n-1)\rho^n\pi_0$$

Mas podemos chegar no mesmo resultado com uma forma diferente, utilizando novamente a lei de Little$$E[N_q] = \lambda E[T_q]$$$$E[N_q] = \lambda ( \dfrac{1}{\mu-\lambda}-\dfrac{1}{\mu})
\to E[N_q] =  \dfrac{\lambda}{\mu-\lambda}-\dfrac{\lambda}{\mu}$$
### Qual é a vazão?
É lambda, o que eu vejo entrando é o que eu vejo saindo. $$X = \lambda$$
### Qual é a taxa de utilização do servidor?
Qual é a fração do tempo que o servidor está ocupado? 
O servidor está utilizado em todos os estados menos o 0. A probabilidade dele não estar sendo utilizado é $\pi_0$ 

A probabilidade dele estar sendo utilizado é $1-\pi_0$, ou seja, $\rho$

A utilização do servidor$$Ulitização =1-\pi_0 = 1- (1-\rho) =  \rho = \dfrac{\lambda}{\mu}$$
