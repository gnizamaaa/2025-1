O processo de Poisson é o modelo mais amplamente utilizado para chegas em um sistema. Exitem duas razões para isso:
1. Propriedades Markovianas do processo de Poisson
2. Em muitas situações este é um excelente modelo.
	(a) Redes de comunicação
	(b) Fenômenos físicos
Em geral, o processo se Poisson aparece frequentemente na natureza quando nós estamos observando o efeito "agregado" de um número grande de indivíduos ou partículas operando individualmente.

O agregado tem a distribuição de Poisson porque apesar de ter uma probabilidade individual baixa, por terem muitos indivíduos, o agregado tem uma chance alta. Cada individuo está agindo individualmente.
	Qual é a probabilidade de alguém da sala fazer uma ligação? Baixa
	Qual é a probabilidade de alguém da UFES fazer uma ligação? Alta

## Definição incrementos independentes
	N(t) é o número de eventos que ocorreram até o instante de tempo t.
Uma sequência de eventos tem **incrementos independentes** se o  número de eventos que ocorrem em dois intervalos de tempo **disjuntos** são independentes. Mais especificamente, para todo $t_0 \lt t_1 \lt t_2 \lt ... \lt t_n$ , as variáveis aleatórias $$N(t_1)-N(t_0), N(t_2)-N(t_1),..., N(t_n)-N(t_{n-1}),$$
são independentes
### Exemplos
1. Pessoas entrando em uma loja **sim**
	1. Supondo que ela seja 24/7 e seja em sp (ninguém dorme) ela tem incrementos independentes.
	2. Se ela está fazendo promoção, em que o quanto chegou vai intervir na próxima leva de pessoas, não terá incrementos independentes.
2. Nascimento de crianças em Itaguaçu **sim**
	1. Se for levar em consideração um carnaval por exemplo, ainda será independente.
	2. Se levar em consideração que um pico gerará um outro pico 30 anos depois, será dependente.
	3. Se for abstrair que um interfere no outro, será independente.
3. Gols marcados pelo centro avante do seu time **não**
	1. Um individuo, um único ponto é muito difícil modelar bem como Poisson
	2. A habilidade do indivíduo seguirá aproximadamente a mesma. Nenhum gol em um intervalo, indicará que provavelmente o próximo não fará nenhum gol. (Não tem incremento independente)
	3. Só seria independente se todos os gols fossem feitos apenas dependente de sorte, algo como ??? Gol de goleiro

## Definição incrementos estacionários
Uma sequência de eventos tem **incrementos estacionários** se o número de eventos que ocorrem em um intervalo de tempo depende somente do tamanho do intervalo e não do seu começo. Isto é, $N(t+s)-N(s)$ tem a mesma distribuição para todo s.
O fluxo de pessoas naquela loja é constante

O nascimento de crianças em Itaguaçu, considerando o carnaval, será independente Mas **não será estacionário**.
	Vai depender de onde eu coloco o início do nosso período.
Mesma coisa considerando que as pessoas dormem no caso da loja.


# Definindo Processo de Poisson
Um processo de Poisson tendo razão $\lambda$ é uma sequência de eventos tais que:
1. N(0) = 0 (antes da loja abrir ninguém estava nela)
2. Incrementos independentes
3. O número de eventos em qualquer intervalo de tamanho t segue uma distribuição de Poisson com média $\lambda t$. Isto é, $\forall s,t \ge 0$  $$Pr\{N(t+s)-N(s)=n\} = \dfrac{e^{-\lambda t} (\lambda t)^n}{n!} ;\ \ n=1,2,3,..$$
	(Vai ser estacionário, não tem s do outro lado da equação, não interessa onde o intervalo começa só o tamanho do intervalo t)

Distribuição de Poisson é uma **distribuição discreta**, não tem como calcular probabilidade de n=1.1. O n tem que ser um número discreto; t e lambda podem ser reais
É bom para número de eventos que ocorrem em uma quantidade de tempo
## Exercício
Pessoas chegam ao ponto da UFES com uma média de 3 pessoas/minuto.
Qual é a probabilidade de que em um intervalo de tempo de 10 minutos cheguem 20 pessoas no ponto? (Assuma que o processo de chegada é de Poisson) $$Pr\{N(10+s)-N(s) =20\} = \dfrac{e^{-30}(30)^{20}}{20!} = 0.0134$$
O processo de chegada de pessoas ao ponto da UFES pode ser modelado como um processo de Poisson com razão $\lambda$ de 3 pessoas por minuto. Se Talles acabou de chegar no ponto, qual é a probabilidade da próxima chegada ocorrer depois de 5 minutos?

$$Pr\{N(5+s)-N(s) =0\} = \dfrac{e^{-15}(15)^{0}}{0!} = e^{-\lambda t}$$

> [!Fique com essa]
> A grande sacada é que se o processo de chegada é de Poisson, o intervalo entre chegadas é exponencial, segue a distribuição exponencial
> Assim será Markoviano

