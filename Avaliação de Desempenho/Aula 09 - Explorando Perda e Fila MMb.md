Pr_{Perda}
$$Pr_{perda} = \pi_b = \pi_0 \rho^b = (\dfrac{\rho-1}{\rho^{b+1}-1})\rho^b$$

Para o exemplo de $\lambda=2 \mu=1$  (e originalmente tentando obter $Pr_{perda}\le0.1$ )
Não tem como diminuir de 50% a probabilidade de perda, o mínimo é 50% por maior que seja a fila
Isso pela fórmula $$Pr_{perda}= \dfrac{1}{2-\dfrac{1}{2^b}}$$A curva parece um pouco exponencial mas vai para uma assintótica para 0.5 (meio) se plotar b X Perda

Lambda mt grande com mu muito pequeno, não dá para ter uma perda menor


# Modelando o RU com b funcionários servindo (Fila M/M/b)
São b funcionários iguais com uma fila única
$$\begin{align}Poisson(\lambda) \to |||||]\to  &(\mu) \to\\\
&(\mu) \\\
&(\mu)
\end{align}$$

## Condição de equilíbrio
A condição de equilíbrio nesse caso será $\lambda \lt b\mu$, caso contrário a fila vai crescer para o infinito
$$\rho=\dfrac{\lambda}{b\mu}$$
## Diagrama de transição de estados (DTE)
Passa para o estado da frente com a razão de $\lambda$
Passa do estado 1 para o 0 com razão $\mu$
Passa do estado 2 para o 1 com razão $2\mu$
	Não há uma transição de estado de 2 para 0, isso porquê teriam que os dois terminarem ao mesmo tempo, o que não é possível, estamos analisando de forma em que 2 eventos não acontecem no mesmo tempo
	
**O que é o estado 2?** 
	É o estado em que está com 2 servidores ocupados, vai passar para o estado 1 se uma terminar OU a outra terminar
	
Isso vai seguindo sendo do estado 3 para 2 com 3\mu , 4 para 3 com 4\mu ...

**(b+1 -> b)** Até chegar em $b+1$ para b, que seguirá sendo $b\mu$
	b servidores estão ocupados e 1 está na fila
E seguirá assim para frente, $b+2$ para $b+1$ vai ser $b\mu$
$b+3$ para $b+2$ será $b\mu$
![[Pasted image 20250602104132.png]]

# O estado de equilíbrio (Kirchhoff)
O que sai = o que entra 

Estado 0: $$\lambda \pi_0 = \mu \pi_1 \therefore \pi_1 =\dfrac{\lambda}{\mu} \pi_0$$
Estado 1: $$\lambda \pi_1 + \mu \pi_1 = \lambda \pi_0 +2 \mu \pi_2 \therefore \pi_2= \dfrac{\lambda}{2\mu} \pi_1 \therefore \pi_2 = \dfrac{1}{2} (\dfrac{\lambda}{\mu})^2 \pi_0$$
Estado 2: $$\lambda \pi_2 + 2\mu \pi_2 = \lambda \pi_1 +3 \mu \pi_3 \therefore \pi_3= \dfrac{\lambda}{3\mu} \pi_2 \therefore \pi_3 = \dfrac{1}{6} (\dfrac{\lambda}{\mu})^3 \pi_0$$
Isso vai seguir até b-1 (\pi_b ainda segue a regra) $$\lambda \pi_{b-1} + (b-1)\mu \pi_{b-1} = \lambda \pi_{b-2} +({b\mu}) \pi_b \therefore \pi_b \dfrac{\lambda}{b\mu} \pi_{b-1} \therefore \pi_b = \dfrac{1}{b!} (\dfrac{\lambda}{\mu})^b \pi_0$$
E como seria para o estado b? Em que há mudança de o que entra?$$\lambda\pi_b+(b\mu)\pi_{b} = \lambda\pi_{b-1}+(b\mu)\pi_{b+1} \therefore \pi_{b+1}=\dfrac{\lambda}{b\mu}\pi_b \therefore \pi_{b+1}= \dfrac{1}{b}\dfrac{1}{b!}(\dfrac{\lambda}{\mu})^{b+1}\pi_0$$

Estado b+1:
$$\lambda\pi_{b+1}+(b\mu)\pi_{b+1} = \lambda\pi_{b}+(b\mu)\pi_{b+2} \therefore \pi_{b+2}=\dfrac{\lambda}{b\mu}\pi_{b+1} \therefore \pi_{b+2}= \dfrac{1}{b^2}\dfrac{1}{b!}(\dfrac{\lambda}{\mu})^{b+1}\pi_0$$
Generalizando:
$$\pi_n = \dfrac{1}{b\mu}\pi_{n-1} \therefore \pi_n = \dfrac{1}{b^{n-b}}\dfrac{1}{b!}(\dfrac{\lambda}{\mu})^n \pi_0$$


$$\pi_n = \begin{cases}
\dfrac{1}{n!}(b\rho)^n\pi_0  &; n\lt b\\
\dfrac{b^b}{b!}\rho^n\pi_0&; n\ge b
\end{cases}$$

Para achar \pi_0 iremos usar a informação de que: $$\sum_{n=0}^{\infty} \pi_n = 1$$
Isso pode ser escrito como:$$\sum_{n=0}^{b-1} \pi_n  + \sum_{n=b}^{\infty} \pi_n= 1$$

E assim:
$$\sum_{n=0}^{b-1} \dfrac{1}{n!}(b\rho)^n\pi_0  + \sum_{n=b}^{\infty} \dfrac{b^b}{b!}\rho^b\pi_0= 1$$

Podemos retirar o desnecessário de dentro do somatório $$\pi_0[\sum_{n=0}^{b-1} \dfrac{1}{n!}(b\rho)^n  + \dfrac{b^b}{b!} \sum_{n=b}^{\infty} \rho^b]= 1$$
Resolvendo o primeiro somatório, sabendo que $\rho$ tem a restrição por tem que servir a condição de equilíbrio
$$\pi_0[\sum_{n=0}^{b-1} \dfrac{1}{n!}(b\rho)^n  + \dfrac{b^b}{b!} \dfrac{\rho^b}{1-p}]= 1$$
$$\pi_0 = [\sum_{n=0}^{b-1} \dfrac{1}{n!}(b\rho)^n  + \dfrac{b^b}{b!} \dfrac{\rho^b}{1-p}]^{-1}$$

## Qual é a probabilidade de existir fila no sistema M/M/b? 
A probabilidade disso acontecer vai ser a probabilidade de estar em um estado maior que b, isso é:
$$Pr_Q = \pi_{b+1}+\pi_{b+2}+... = \sum^{\infty}_{n=b+1}\pi_n = \sum^{\infty}_{n=b+1}\dfrac{b^b}{b!}\rho^n\pi_0$$
$$Pr_Q = \dfrac{b^b}{b!} \pi_0 \sum^{\infty}_{n=b+1}\rho^n = \dfrac{b^b}{b!}\pi_0\dfrac{\rho^{b+1}}{1-\rho}$$

## Quanto é $E[N_Q]$ ?
Quanto será o número médio de trabalhos na fila?
$$E[N_Q] = \sum^{\infty}_{n=b+1}(n-b)\pi_n$$
n-b -> Quantidade na fila
b+1 -> Estado em que começa a se ter fila

$$E[N_Q] = \sum^{\infty}_{n=b+1}(n-b)\pi_n = \sum^{\infty}_{n=b+1}(n-b)\dfrac{b^b}{b!}\rho^n\pi_0 =\dfrac{b^b}{b!}\pi_0\sum^{\infty}_{n=b+1}(n-b)\rho^n $$

Esse somatório será $1\rho^{b+1} + 2\rho^{b+2}+3\rho^{b+3}+4\rho^{b+4}...$ Ou seja, podemos escrever como:$$E[N_Q] =\dfrac{b^b}{b!}\pi_0\sum^{\infty}_{n=1}n\rho^{b+n}$$$$E[N_Q] =\dfrac{b^b}{b!}\pi_0\sum^{\infty}_{n=1}{n\rho^{b}*\rho^n} $$$$E[N_s] =\dfrac{b^b}{b!}\rho^{b}\pi_0\sum^{\infty}_{n=1}{n\rho^n}$$
E assim podemos resolver o somatório: $$E[N_Q] =\dfrac{b^b}{b!}\rho^{b}\pi_0 \dfrac{\rho}{(1-\rho)^2}$$
E então simplificar $$E[N_Q] =\dfrac{b^b}{b!}\rho^{b+1}\pi_0 \dfrac{1}{(1-\rho)^2}$$

Ou seja: $$E[N_Q] =\dfrac{b^b}{b!}\rho^{b+1}\pi_0 \dfrac{1}{(1-\rho)}*  \dfrac{1}{(1-\rho)}$$

E então observar exatamente que: $\dfrac{b^b}{b!}\rho^{b+1}\pi_0 \dfrac{1}{(1-p)}$ é Exatamente a Pr_Q, a probabilidade de fila que tínhamos calculado