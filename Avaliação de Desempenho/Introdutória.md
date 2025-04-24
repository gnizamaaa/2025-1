O que estudaremos nesse curso?
Primeiro ponto é, aparentemente, sobre como escalar uma plataforma, um sistema
Segundo, capacidade de atendimento
Terceiro, como aumentar o fluxo

- Sistemas mais comuns que iremos tratar: Servidor web, de banco de dados, fazenda de servidores web
- Consumidores: Requisições web, consultas ao banco
Mas se aplica a qualquer situação que tem contingência, que tem fila

# Primeiro Exemplo
Considere um exemplo em que estaremos duplicando a razão de chegada, o fluxo de usuários e por consequência a razão média de chegadas ao servidor, de uma dada plataforma na próxima semana, como podemos lidar com isso de forma que os usuários não sintam uma grande diferença no tempo de processamento//acesso?
	Levando em conta o banco de dados, buscas, filtragens...
Como podemos assegurar que os clientes observem o mesmo tempo de resposta médio?
Qual deveria ser a velocidade da CPU de modo a manter o mesmo tempo médio de resposta?
	Não fazer nada não é uma alternativa, mas o que será que deve ser feito? Em que podemos atuar? Trocando o servidor por um mais rápido, mas o quão mais rápido?
	
Duplicar o CPU vai fazer com que tenha METADE do tempo de resposta anterior, mesmo com o dobro de requisições.
	As coisas não escalam linearmente, da mesma forma, mantendo o mesmo processamento o tempo de resposta facilmente explodiria
O ideal nesse cenário é **AUMENTAR 50%**, mas esse resultado não vem fácil, não é intuitivo

A maior parte do curso vai ser quebrando essas intuições padrões

# Segundo Exemplo
Throughput (vazão) == Lucro
Estamos em uma padaria em que o caixa é lento, eficiente, barrando a vazão, a quantidade de clientes que a padaria consegue atender.
	Trocando o servidor, o caixa, pode simplesmente não aumentar a vazão.
	A vazão só depende da razão de chegada, trocar o servidor por um servidor mais rápido não altera a vazão.

Para aumentar a vazão devemos, aumentar a razão média de chegada, fazer uma propaganda, uma promoção por exemplo
	Em um sistema aberto a vazão só depende da razão média de chegada
	
Aumentar a velocidade não vai aumentar a sua vazão, só vai fazer o servidor ficar mais tempo ocioso.
	Só vai diminuir o tempo médio de resposta, o tempo de atendimento necessário
	
Isso só vale para situações em que estamos em **equilíbrio, em que a razão média de chegada é menor que a razão média de serviço**
	Sendo a razão média de serviço, a quantidade de clientes que o atendente consegue atender por minuto por exemplo, de forma que não é uma fila que vai para o infinito, que entra mais cliente que consegue ser atendido
	Se a razão estiver igual, o sistema estará instável, repare que essa é uma MÉDIA, logo terão horários em que chegam muitos e outros pouco.
	
Essa flutuação das razões é o que causa fila em uma situação de equilíbrio.

Quando um sistema não está em equilíbrio aumenta o throughput, vazão, mas isso somente porque a fila estava tendendo ao infinito.
