É inviável utilizar uma comunicação de internet tradicional que é síncrona (que todo get tem response) e unicast (vai para apenas 1 destino)
	Além de que precisa de socket, ip, porta, coisas não fáceis/transparentes ao desenvolvedor
Precisa de uma abstração para se falar com um conjunto de entidades sem precisar saber exatamente o endereço de cada

# MQTT
Message Queue Telemetry Transport 
Funciona baseado em uma entidade responsável por gerenciar uma fila de mensagens e para essa fila de mensagens eu vou distribuir a quem tá interessado nessa mensagem

## Modelo Publish/Subscribe
Aparece uma entidade Broker
	Os clientes publicam as mensagens, com um tópico definido, para o broker (único que é necessário saber o IP e porta)
	O broker enfileira essas mensagens
	Os dispositivos se inscrevem no tópico que as interessa, recebendo as atualizações(mensagens) do broker. 
	Só quem assina o tópico recebe as mensagens
	
Por baixo dos panos o Broker mantém uma conexão TCP/IP com todo mundo ainda
Mosquitto -> Broker simples

Por padrão é apenas um broker, fazendo uma topologia estrela. Mas existem brokers que permitem utilizarmos mais de um broker, desde que eles estejam conectados entre si.

Existe uma diferença de QoS (Quality of Service) 
0 -> Foda-se garantia
2-> Sub que está online recebeu a mensagem

Broker por padrão não guarda nenhuma mensagem
# Estrutura de tópicos
Tem como se inscrever como se fosse diretório também, tem uma estrutura hierárquica dentro do tópico
casa/lampada
casa/fogao
casa/# -> Se inscreve em todos subtópicos de casa

Quanto um mosquitto aguenta na
Varia o tamanho da mensagem e vê o tempo de resposta, quantos clientes subscribed e tal consegue aguentar
	Quanto é o máximo que aguenta sozinho (1 cliente 1 sub)
	Quanto é o máximo que aguenta sozinho (1 cliente 1 sub)

É um bom bonus colocar em docker para isolar quem é quem
Deve ser bom usar um RPi para broker (até porquê vai aguentar menos)

Tem que descobrir o limite e ter gráfico de como foi usando CPU e memória

Seminário 2 -> Escalabilidade Mosquitto

