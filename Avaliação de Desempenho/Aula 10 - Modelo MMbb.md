Não há fila
É o modelo usado para uma central telefônica tradicional por exemplo, o tom tocar é que tinha uma linha disponível e que você havia sido alocado a ela. Não há uma fila para quem não está em uma linha.
# No diagrama de Transição de Estado
Irá acabar em b, porquê é o ultimo estado do sistema, a partir daquele estado será rejeitado o trabalho
- Para frente vai com razão $\lambda$
- Para trás, como o número de servidores é igual ao número de possíveis vai ser sempre cada seguinte forma
1->0 = $\mu$, 2->1 = $2\mu$, 3->2 = $3\mu$, 4->3 = $4\mu$,..., b->b-1 = $b\mu$

Por ser uma cadeia de Markov, não se olha para o passado, só interessa o presente
	Se fosse de ordem 2 por exemplo se olharia também o estado anterior, mas não é o caso

Repare também que nesse estado, não há fila todo trabalho no servidor estará sendo atendido.

> [!Observação]
> Todas essas filas são uma cadeia de Markov contínua, a transição de estados pode ocorrer a qualquer momento. Diferente de algo que só troca de estado em um certo momento estável, algo como todo dia a noite, como por exemplo "O que eu comerei hoje sabendo que ontem eu comi x"

## Analisando os estados (equações de equilíbrio)
Estado 0: $$\lambda \pi0 = \mu \pi_1 \therefore \pi_1 = \dfrac{\lambda}{\mu}\pi_0$$
Estado 1: $$\lambda\pi_1 + \mu\pi_1=\lambda \pi_0 + 2\mu\pi_2 \therefore \pi_2 = \dfrac{\lambda}{2\mu}\pi_1 \therefore \pi_2 = \dfrac{1}{2}(\dfrac{\lambda}{\mu})^2 \pi_0$$
Estado 2:$$\lambda\pi_2 + 2\mu\pi_2 = \lambda\pi_1 + 3\mu\pi_3 \therefore \pi_3 = \dfrac{\lambda}{3\mu}\pi_2 \therefore \pi_3 = \dfrac{1}{6}(\dfrac{\lambda}{\mu})^3\pi_0$$
Estado n: $$\pi_n=\dfrac{1}{n!}(\dfrac{\lambda}{\mu})^n\pi_0\ \ \ ;\ n\le b$$
## Encontrando uma fórmula fechada para $\pi_0$
Sabendo que o sistema TEM QUE ESTAR EM ALGUM ESTADO$$\sum^b_{n=0}\pi_n=1$$
Substituindo o $\pi_n$:$$\pi_0\sum^b_{n=0}\dfrac{1}{n!}(\dfrac{\lambda}{\mu})^n=1$$
$$\pi_0 = \dfrac{1}{\sum^b_{n=0}\dfrac{1}{n!}(\dfrac{\lambda}{\mu})^n}$$
# Qual é a probabilidade de Bloqueio?
Sabendo que você só entra se tiver um caixa desocupado e que você acabou de chegar no sistema, qual é a probabilidade de você ser negado de atendimento
É a probabilidade de um cliente ser perdido, probabilidade de perda
$$Pr_{perda} = \pi_b$$
É igual a probabilidade do sistema estar no último estado, o estado b
Isso é
$$\pi_b = \dfrac{1}{b!}(\dfrac{\lambda}{\mu})^b \pi_0$$

$$\pi_b = \dfrac{1}{b!}(\dfrac{\lambda}{\mu})^b [\sum^b_{n=0}\dfrac{1}{n!}(\dfrac{\lambda}{\mu})^n]^{-1}$$
Essa é a fórmula B.Erlang

Obs: Por conta dessa fórmula, quando há $\pi_0$ grande não há $\pi_b$ grande.
## Problema comum
Tendo um $\lambda$ e tendo um $\mu$ e uma meta de máximo de perda, queremos encontrar o número mínimo de servidores, número mínimo de b para que atenda o controle de qualidade

Para resolver as fórmulas, por serem muito complexas algebricamente, muitas vezes utilizamos pesquisa binária, começa com um valor, vê se tá grande ou pequeno e muda o b, vê o resultado... Repetindo até encontrar o valor mínimo de b que satisfaz.
	Também temos calculadoras de B.Erlang online, em que se dá 2 das variáveis (b, $\lambda$, $\mu$) e se descobre a terceira
## Desenhando graficamente o sistema
$$\begin{align}Poisson(\lambda) \to  &(\mu) \to\\\
&(\mu) \\\
&(\mu)_{(b)}
\end{align}$$

# Outros problemas com modelagem diferente
Tempo de serviço é uma variável aleatória, por isso se é um caixa de autoatendimento de supermercado, em que flutua a quantidade de itens de cada cliente e velocidade de cada cliente
	Se fosse um tempo constante não seria Markoviano (exponencial) no segundo M representando o tempo de serviço, seria constante
	Também seria outro modelo se tivesse uma fila para cada servidor
	Também não pode considerar que há uma escolha de sempre estar entrando na menor fila 
	
Se tiver uma diferença estável de razão de chegada entre os servidores, com filas separadas tem como modelar como várias instâncias de M/M/1.
![[8a1f62f6-8ab1-46a6-8255-4d51ae73e04e.jpeg]]

#### Tangenciando para pensar sobre a aplicação no mundo
Sabendo que tem um horário de pico muito marcante é interessante muitas vezes dividir em dois problemas para que possa ser melhor dimensionado
	Colocar 2/3 caixas no mercado em horário vazio e 15 em horário de pico.
Para isso basta fazer um lambda diferente para essas duas faixas de horário por exemplo
Mas toda essa adaptação irá depender também de custo, situação, importância, vários fatores

No curso a gente vê a parte técnica, não da parte administrativa.