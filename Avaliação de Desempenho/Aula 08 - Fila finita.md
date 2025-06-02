# De volta ao começo
O exemplo motivacional que foi utilizado no começo do nosso curso
**Recordando**: A razão média de chegada duplicará. Qual deve ser a nova razão média de serviço, para que os usuários percebam o mesmo tempo de resposta antes que a promoção começasse?

$\lambda ^* = 2\lambda$
$\mu ^* = ?$ $$E[T_s^{antes}]=\dfrac{1}{\mu-\lambda}$$ $$E[T_s^{depois}]=E[T_s^{antes}]$$ $$E[T_s^{depois}] = \dfrac{1}{\mu^* - 2\lambda}$$
$$\dfrac{1}{\mu - \lambda} = \dfrac{1}{\mu^* - 2\lambda} \to \mu^*-2\lambda=\mu-\lambda$$
$$\mu^* = \mu + \lambda$$

### Dando números
Suponha que $\lambda$ =10 clientes/minuto e $\mu$ = 20 clientes/minuto.
Logo o tempo de resposta antes da promoção é $E[T_s] =0.1min = 0.6seg$.
Se nada for feito o tempo de resposta, depois do começo da promoção será $E[T_s] = \infty$.

Se nós trocarmos o servidor por um duas vezes mais rápido então o tempo de resposta, depois do começo da promoção, será $E[T_s] = 0.05min = 3seg$.

Se nós trocarmos o servidor por um cuja razão média de serviço é 30 clientes/min, então o tempo de resposta é o mesmo!

Suponha que você esteja modelando um roteador. Talvez a primeira pergunta que você deve se fazer é: A fila M/M/1 é um modelo adequado? Existe um aspecto do roteador que não é, em muitas situações, convenientemente capturado pelo modelo - a fila é **finita**.
	No M/M/1 a fila é infinita, não tem como modelar a pergunta de "Qual é a probabilidade de um pacote ser perdido, probabilidade de dropar o pacote pela fila estar cheia"
	**Qual é a probabilidade de perda?**, Quantos datagramas, pacotes, você precisa ser capaz de armazenar para ter uma probabilidade de tanto?

> Nem se forem dois servidores iguais uma situação M/M/2 se comporta como 2 M/M/1, apenas se tiverem filas separadas

Qual é a quantidade de telefonistas e circuitos que preciso para que alguém que queira fazer uma ligação em uma região tenha uma chance maior de 90% de ser servido.

# A Fila M/M/1/b
Chegada Poisson, Serviço Exponencial, 1 servidor, b vagas **no sistema** (posso ter b trabalhos no sistema, b-1 na fila e 1 no servidor)

Aqui $\lambda$ não precisa necessariamente ser menor do que $\mu$, apenas irá gerar uma perda enorme mas não vai gerar uma fila infinita

$\lambda \to[||||||](\mu)\to$ 

Como fica o diagrama de Transição Estado da Fila M/M/1/b?
	Fica parecido com o anterior mas com estados limitados, o ultimo (b) só tem transição para b-1 e b
Obs: na foto já está simplificado (sem os delta multiplicando)

Tem que obedecer Kirchoff ainda para ser estável, não estar flutuando

0: $$\lambda \pi_0 = \mu \pi_1\ \therefore \ \pi_1 = \dfrac{\lambda}{\mu}\pi_0$$
1:$$\lambda \pi_1 +\mu \pi_1 = \lambda \pi_0 + \mu \pi_2\ \therefore  \ \pi_2 = \dfrac{\lambda}{\mu}\pi_1 \ \therefore \ \pi_2=(\dfrac{\lambda}{\mu})^2 \pi_0$$
2:$$\lambda \pi_2 +\mu \pi_2 = \lambda \pi_1 + \mu \pi_3\ \therefore  \ \pi_3 = \dfrac{\lambda}{\mu}\pi_2 \ \therefore \ \pi_3=(\dfrac{\lambda}{\mu})^3 \pi_0$$

b-1:$$\pi_b=(\dfrac{\lambda}{\mu})^b \pi_0$$

O sistema não é linearmente independente, não é possível resolver ele

Novamente precisamos lembrar que o sistema **TEM QUE ESTAR EM ALGUM ESTADO** $$\sum^b_{n=0}\pi_n =1$$
Assim temos que: $$\sum^b_{n=0}(\dfrac{\lambda}{\mu})^n \pi_0 =1$$
$$\pi_0 \sum^b_{n=0}(\dfrac{\lambda}{\mu})^n =1$$
$$\pi_0  =\dfrac{1}{\sum^b_{n=0}(\dfrac{\lambda}{\mu})^n}$$

Isso irá convergir para: $$\pi_0 = \dfrac{(\dfrac{\lambda}{\mu})-1}{(\dfrac{\lambda}{\mu})^{b+1}-1} $$
É uma P.G finita, irá convergir de qualquer jeito, sempre tem uma resposta fechada, independente de $\rho$, que é $\lambda/\mu$, ser maior que 1.
Podemos reescrever lembrando de $\rho$, para facilitar
$$\pi_0 = \dfrac{\rho-1}{\rho^{b+1}-1} $$

Qual é a probabilidade de perda? É a probabilidade de estar em \pi_b
$$Pr_{perda} = \pi_b = \rho^b (\dfrac{\rho -1}{\rho^{b+1} -1})$$
	A definição sendo, dado que chegou um pacote, qual a probabilidade de o pacote ser dropado
## Exemplo numérico
$\lambda = 10 pacotes/seg\ \ \ \mu = 12.5 pacotes/seg$
$Pr_{perda} \le 0.1$ 
Qual deve ser o tamanho da fila para que a probabilidade de perda seja atendida
$\rho = 10/12.5 = 0.8$
$$(0.8)^b (\dfrac{0.8-1}{(0.8)^{b+1}-1}) =0.1  \to b = \lceil 4.61416\rceil \to b=5 $$

Dica para resolver sem precisar do Wolfram é chutar um valor para b e ver se tá grande ou pequeno, ir fazendo uma busca binária 

E para um $\rho$ maior que 1? Como isso ficaria?
$$(2)^b (\dfrac{2-1}{(2)^{b+1}-1}) =0.1  \to b = \lceil 4.92334\rceil \to b=5 $$

![[Pasted image 20250528104806.png]]



**Razão efetiva de chegada $\lambda ^*$**: A razão dos trabalhos que chegam e conseguiram entrar
	Do pacotes que chegaram, quantos conseguiram entrar?
	Os pacotes que chegaram e entraram
	$$\lambda^* = \lambda * (1-\pi_b) \to \lambda^* = \lambda - \lambda\pi_b $$
	Os que chegaram e que não foram dropados, bloqueados
	
Os que chegaram e não conseguiram entrar seriam $\lambda \pi_b$ 

O tempo médio de resposta do sistema vai considerar apenas quem será de fato atendido se for usar Lei de Little.
	Vai sair do sistema apenas $\lambda^*$, o que entra nele não é $\lambda$ 


