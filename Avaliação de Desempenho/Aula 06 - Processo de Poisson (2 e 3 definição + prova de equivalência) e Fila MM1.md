## Exercício
Alunos chegam ao RU de acordo com um processo de Poisson, a uma razão de 5 por minuto. Vinícius acabou de chegar ao RU.
Qual é a probabilidade de que a próxima chegada ocorra depois de três minutos?

X -> Variável aleatória representando o intervalo de tempo entre chegadas sucessivas.

O que o exercício está perguntando?
	$Pr\{X\gt 3\} = Pr\{N(3+s)-N(s) = 0\}$ 
Por ser um processo de Poisson, podemos calcular isso $$Pr\{N(3+s)-N(s) = 0\} = \dfrac{e^{-\lambda t}*(\lambda t)^n}{n!}_{n=0,\lambda =5, t=3} = e^{-\lambda t} \to e^{-15}$$Qual é a distribuição probabilística que a variável aleatória X segue?
	Como X segue $e^{-\lambda t}$, X é uma exponencial com razão $\lambda$.
	
# Definição 2 - Processo de Poisson
Um processo de Poisson com razão é uma sequência de eventos tais que o intervalo entre chegadas sucessivas são variáveis aleatórias que seguem uma **distribuição exponencial** com razão $\lambda$ e $N(0)=0$.
## Prova: Definição 1 $\implies$ Definição 2
Vimos que o caminho partindo da distribuição implica que o intervalo entre chegadas sucessivas são variáveis aleatórias que seguem uma distribuição exponencial no **exercício anterior**.
## Prova: Definição 2 $\implies$ Definição 1
Não é trivial essa prova, mas está no Livro (Feller, vol.2, pg.11)

# Definição 3 - Processo de Poisson
Nós escrevemos $f(\delta) = o(\delta)$ sss $[\lim_{\delta \to 0}\dfrac{f(\delta)}{\delta}] = 0$ 

*(a dentro do parenteses tem que crescer mais devagar que a de fora, isso pelo little o)* -> N tenho certeza dessa frase, é uma anotação
Por exemplo, $f(\delta)=\delta^2$ então $f(\delta)=o(\delta)$.

Um processo de Poisson tendo razão $\lambda$ é uma sequência de eventos tais que:
	1. $N(0)=0$
	2. O processo tem incrementos estacionários e independentes
	3. $Pr\{N(\delta)=1\} = \lambda \sigma + o(\delta)$ -> A probabilidade de acontecer um evento em um intervalo pequeno de tempo é "$\lambda \delta$"
	4. $Pr\{N(\delta)\ge 2\} =o(\delta)$ -> Em um intervalo pequeno, a probabilidade de acontecer mais de um evento é praticamente 0
($o(\delta)$ é muito pequeno, podemos considerar 0 para o entendimento)

## Esboçando uma pequena prova de equivalência
Obs.: Isso daqui não possui grande relevância para a matéria, mas apenas para credibilizar a 3^a definição 

Lembrando que:
$e^a = \dfrac{a^0}{0!} \dfrac{a^1}{1!} \dfrac{a^2}{2!} \dfrac{a^3}{3!} +...$
 Qual é a probabilidade de acontecer **um** evento em um intervalo de tempo pequeno?$$ Pr\{N(\delta+s)-N(s)=1\}=e^{-\lambda \delta}(\lambda \delta) = (\lambda \delta)[\dfrac{(-\lambda \delta)^0}{0!}+\dfrac{(-\lambda \delta)^1}{1!}+\dfrac{(-\lambda \delta)^2}{2!}+...]$$
 Isso é $$ = (\lambda \delta) - \dfrac{(\lambda \delta)^2}{1!} + \dfrac{(\lambda \delta)^3}{2!} + ...$$
 Por causa do $\delta$ ser tão próximo de 0, ele elevado irá ainda mais rápido para 0, por isso podemos colocar o little o, que vai se aproximar de 0$$=\lambda\delta +o(\delta)$$

# A fila M/M/1 (M/M/c)
## Notação de Kendall 
\_/\_/\_/\_/\_
O primeiro slot é o **Processo de Chegada**
O segundo slot é **Tempo de Serviço**
O terceiro slot é o **Número de servidores no sistema**, uma constante
(O quarto e quinto slot são opcionais)
O quarto slot é o **Limite para o tamanho da fila**, por padrão (se não colocar) é infinito
O quinto slot é a **População a ser atendida**, por padrão (se não colocar) é infinito

### Exemplo: 
M/M/1/$\infty$/4000     
1. Processo de chegada M (Markoviano, é de Poisson)
2. Tempo de serviço M (Markoviano, é distribuição Exponencial por ser a distribuição contínua)
	- D por exemplo significaria determinístico, o roteador leva exatamente x tempo para rotear um pacote
	- $Er_2$ probabilístico mas com distribuição de Erlang de ordem 2
	- G é o geral, em que se sabe a média, talvez o desvio padrão. Mas o G é de geral, quando não se conhece a distribuição.
3. Possui apenas um servidor para suprir a demanda da fila
4. Possui uma fila infinita, que pode crescer infinitamente
5. Possui uma população de 4000 indivíduos que pode gerar eventos (gerar pacotes, gerar chamadas, chegar a uma fila)

## Entendendo a fila M/M/1 (M/M/1/$\infty$/$\infty$)
O essencial é definir o estado do sistema, a coisa mais importante.
O que é o estado do sistema nessa situação? 
	Para um roteador modelado com fila M/M/1-> Número de pacotes no roteador
	Para o RU -> Numero de alunos na fila+atendendo
Podemos ter o estado 0 (vazio), 1,2,3,4,5,6,7...
O sistema pode estar em qualquer um desses estados

A probabilidade do sistema passar de 0 para 1, é a probabilidade da distribuição de chegada chegar 1 indivíduo em um intervalo de tempo PEQUENO ($\lambda \delta +o(\delta)$). 
E de passar 0 para 2 $o(\delta)$, quase 0, você não passa de 0 para 2, não passa de 0 para 3.

Em um pico segundo não se chega 2,3 alunos.

A probabilidade de 0 se manter em 0 é $1- \lambda \delta$ .

A probabilidade de do estado 1, passar para o estado 2, é $\lambda \delta$ pelo mesmo motivo

Agora teremos que ligar com o tempo de serviço que segue distribuição exponencial $\mu$ ,
como agora será contínuo, temos que a probabilidade de 1 sair para 0 é de $\mu \delta$.
	Obs.: O mesmo de "sair 2 ao mesmo tempo" ocorre aqui.

E a probabilidade de se manter em 1 é a probabilidade de não chegar ninguém nem sair ninguém, isso é $1- \lambda \delta -\mu \delta$, ou seja $1- (\lambda + \mu)\delta)$ .

Vai ficar mais claro vendo o diagrama.
### DTE-CMTC
Veja o Diagrama de Transição de Estado de uma Cadeia de Markov de Tempo Contínuo (DTE-CMTC)
É cadeia de Markov porquê só depende do seu estado atual, não importa qual foi "o caminho"

Considerando apenas a chegada (sem o tempo de serviço), sem conclusão de serviços 
![[WhatsApp Image 2025-05-21 at 10.49.27 AM.jpeg]]

Agora considerando a conclusão de serviços também markoviana:
![[WhatsApp Image 2025-05-21 at 10.46.54 AM.jpeg]]
### Obs:
Muito vai nos interessar saber quantas pessoas estarão no sistema, qual a probabilidade de o sistema estar em um estado. (AULA QUE VEM)
Também é importante relevar o estado num regime transiente (abrindo, fechando, picos)
	Isso envolveria equações diferenciais, porquê envolveria taxa de variação