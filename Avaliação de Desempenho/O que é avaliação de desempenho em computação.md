Avaliação de desempenho, para nós é o estudo do comportamento das **filas** em redes de computadores e sistemas computacionais
É para questões de ou projetar o sistema ou fazer upgrade de algo

Sistema do mundo real com questões como:
"Nós deveríamos comprar uma CPU mais rápida?"
  |
 V
Será modelado como: (Abstraindo a parte irrelevante, porquê caso contrário será tão complexo quanto o mundo real)
Redes de filas -> (Análise)-> Resultados
  | 
 V
E então traduzido de volta para "Nós deveríamos comprar uma CPU mais rápida?"

Simulação os resultados são difíceis, chatos, de interpretar. 
# Terminologia *(vocabulário)*
## Rede de Servidor Único
Uma rede é feita de servidores, o exemplo mais simples de rede de fila é uma rede com um único servidor.

Trabalhos Chegando -> $\lambda =1/6{ seg}$ -> ||||||]O -> Saída
					             FCFS(FIFO) $\mu =1/3{ seg}$

- Bolinha é o servidor
- [|||||||] -> Fila de tamanho FINITO
	Outro tipo de problema que vai aparecer com as filas de tamanho finito é "Qual é o tamanho da fila para que apenas 10% dos trabalhos sejam "perdidos"?"
- |||||||] -> Fila de tamanho INfinito
## Parâmetros
Atenção que as razões médias não são determinísticas via de regra, na **MÉDIA**, é aquele valor.
- Ordem de Serviço - nesse caso é o FCFS, First Comming First Serviced (FIFO)
	- Poderia ser algo como uma fila com prioridade, ultimo a chegar primeiro a ser atendido (pilha)
- **Razão média de chegada** - (Lambda $\lambda$)
	- É diferente de dizer "A razão de chegada", que é algo fixo, exato
- Tempo **médio** entre chegadas sucessivas - $1/\lambda$
	- Qual é o tempo **médio** para que o próximo cliente chegue na fila, dado que um cliente chegou agora
	- É $1/\lambda$, o inverso da razão média de chegada
- **Tempo de serviço** - (S $S$)
	- Uma variável aleatória, probabilística, representando o tempo gasto pelo servidor para atender um trabalho
	- Quanto tempo vai levar para o caixa me atender em um banco
	- Vai depender de qual serviço será feito, é um beijo? é uma pilha de contas a ser paga?
- **Tempo médio de serviço** - $E[S]$ 
	- Quanto tempo, em média, se leva para atender um serviço
- **Razão média de serviço** - (Mu $\mu$) =  $1/E[S]$ 

## Métricas de desempenho
- **Tempo de resposta** (Tempo no sistema) - $T_R = T_{partida} - T_{chegada}$ 
	- Ainda assim é uma variável aleatória, dependente de cada caso (não é uma média), via de regra estamos interessados no valor esperado do tempo de resposta $E[T_R]$
	- Tempo que o trabalho levou NO SISTEMA, é o tempo total, isso conta a(s) fila(s), conta a entrada, saída, processamento, trabalho. Somando todas as visitas a um mesmo servidor, inclusive.
		- No nosso exemplo simplório, é o tempo na fila + tempo de serviço
	- NÃO CONFUNDIR COM O TEMPO DE SERVIÇO, que é o tempo no servidor por visita
- Valor esperado do tempo de resposta $E[T_R]$
- Tempo de espera - $T_Q$
	- Tempo na fila
- Valor esperado do tempo de espera $E[T_Q]$
Assim podemos já observar que:
$$E[T_R] = E[S]+E[T_Q]$$
Voltando as métricas:
- Número médio de trabalhos no sistema - $E[N_S]$
	- Quantos trabalhos em média estão no roteador em dado tempo, os sendo trabalhados e os na fila
- Número médio de trabalhos na fila - $E[N_Q]$
	- Quantos trabalhos, em média, estão na fila

## Observações
1. Quando $\lambda$ aumenta, todas as métricas de desempenho **aumentam**
	Vai aumentar o tempo de resposta, espera, número médio de trabalhos no sistema
2. Quando $\mu$ aumenta, todas as métricas de desempenho **diminuem**
3. Nós exigimos que $\lambda$ seja menor que $\mu$ $\lambda < \mu$  **(condição de equilíbrio)**
	Se $\lambda > \mu$, então a fila irá para o INFINITO e as métricas de desempenho irão para o infinito junto.
	Se for igual, o sistema estará **INSTÁVEL**
4. Dada a condição de equilíbrio, suponha que $\lambda$ e $\mu$ **são determinísticos**. O que acontecerá com as métricas de desempenho? 
	Não irá ter fila, porquê as variáveis são constantes, determinísticas.
	O tempo de resposta será o tempo de serviço
5. **A fila só ocorre quando há variabilidade**, na razão de chegada ($\lambda$) ou na razão de serviço ($\mu$).
	"Filas resultam da variabilidade da distribuição do tempo entre chegadas ou do tempo de serviço"
