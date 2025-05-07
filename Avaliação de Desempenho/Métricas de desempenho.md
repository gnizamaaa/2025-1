- Tempo de resposta (Tempo no Sistema) - $E[T_R]$
- Número médio de trabalhos no sistema - $E[N_S]$
- Tempo médio na Fila - $E[T_Q]$
- Número médio de trabalhos na fila - $E[N_Q]$
- Throughput (Vazão) - X

# Mais uma métrica
- Utilização do dispositivo i  - $U_i$
	A utilização do dispositivo i é o tempo que o dispositivo i ficou ocupado durante um período de observação$$ U_i = B/T$$
	Sendo B o tempo que o servidor ficou ocupado e T o tempo de observação

# Lei da Utilização
**Como $X_i$ está relacionado com $U_i$?**
$X_i$ - número de trabalhos concluídos em uma unidade de tempo - Vazão
	$$X_i = C/T$$
	Em que C é a quantidade de trabalhos concluídos 

$$C/T = C/B * B/T$$
$$X_i = C/B * U_i$$

$B/C = E[S]$ -> Tempo médio para o serviço de um trabalho. Para cada trabalho levou x minutos
$C/B = \mu_i$-> Razão média de serviço, quantos x clientes são atendidos a cada y minutos 

Logo a razão entre $X_i$ e $U_i$ é $$X_i = \mu_i * U_i$$
Reformulando levemente, encontramos a Lei da Utilização: $$U_i = X_i/\mu_i$$
# Lei de Little
Suponha que iremos abrir 2 restaurantes, um SlowFood e FastFood.
Esperando que a razão média de chegada $\lambda$ será a mesma
Em qual dos dois restaurantes será necessário mais espaço (mais mesas, cadeiras)?
Sabendo que a razão média é menor no SlowFood$$\mu_{Slow} << \mu_{Fast}$$
Será necessário mais espaço no slow, já que as pessoas vão ficar mais tempo no sistema, ficam mais tempo para o atendimento.
## Definição formal
Para um sistema ergótico (Um sistema em que indivíduos, clientes, não desaparecem, não podem ficar infinitamente no sistema ou saírem por nada. Também não pode ser criado um cliente dentro do servidor. Cliente n pode ser criado ou deletado no sistema) nós temos que $$E[N_S]=\lambda E[T_S]$$Onde $E[N_S]$ é o número esperado de trabalhos no sistema,
$E[T_S]$ é o tempo médio de serviço e 
$\lambda$ é a razão média de chegadas

Se $E[T_S]$ é grande, demora muito para servir, $E[N_S]$ também será grande.
Como os **requisitos são baixos**, podemos usar em muitos lugares e utilizar como uma caixa preta em cima de parte de um sistema por exemplo
### Usando a lei como caixa preta sob partes do sistema
Aplicando em um sistema como:
 $\lambda =1/6{ seg}$ -> ||||||]O -> Saída
$$E[N_S]=\lambda E[T_S]$$
Podemos aplicar também para a FILA! Exatamente porque o sistema da fila também é ergótico$$E[N_Q]=\lambda E[T_Q]$$
	Sendo $E[T_Q]$ o tempo médio na fila

E podemos aplicar só no servidor, sem considerar a fila.
$$E[N_i] = \lambda E[S_i]$$
- $E[N_i]$ -> Numero médio de trabalhos no dispositivo i (servidor)
	- É igual a utilização do servidor, dispositivo i!!!!
- $E[S_i]$ -> Tempo médio de serviço do dispositivo i
	- Que é $E[S_i] = 1/\mu_i$
Podemos usar lambda porque se fosse diferente disso chegando da fila, a fila estaria indo ao infinito, o que não é factível nesse caso (pensando em um sistema estável)

E com isso também podemos concluir que podemos escrever a lei da utilização como:
$$U_i=\lambda/\mu_i$$
# Exercício
Considere o seguinte sistema
 $\lambda =1/6{ seg}$ -> [||||||]O -> Saída

Se fizer uma caixinha cobrindo apenas a fila e servidor (sem a entrada), é um sistema ergótico, mas se colocar a caixa cobrindo a entrada não será ergótico, haverão pacotes descartados porquê a fila é finita.

## Aplicando para esse sistema
$$E[N_S] = \lambda E[T_S]$$
Mas há um problema!!! Não é lambda entrando, é menor que lambda porquê pode haver perda de pacotes quando o sistema estiver cheio
	Logo temos que determinar o que foi perdido

N_i = número de trabalhos no sistema

Haverá uma limitação, em que o N_i vai ser limitado a 8 (conta o que estiver o servidor) nesse caso

A probabilidade de entrar será = Pr{N=0}+ Pr{N=1}+ Pr{N=2}+ Pr{N=3}+ ... + Pr{N=7}
E assim, podemos encontrar um novo lambda!
$\lambda^* = \lambda (Pr\{N=0\}+ Pr\{N=1\}+ Pr\{N=2\}+ Pr\{N=3\}+ ... + Pr\{N=7\})$

## Equilíbrio em uma fila finita
Sabendo que a condição de equilíbrio é ter uma fila infinita
Condição de equilíbrio em uma fila finita = QUALQUER UMA!!!
	$\lambda$ pode ser muito maior do que $\mu$, isso porquê a fila **NUNCA** irá para o infinito
	Isso é porquê a fila é limitada, muito pacote pode ser perdido mas nunca será uma fila infinita
