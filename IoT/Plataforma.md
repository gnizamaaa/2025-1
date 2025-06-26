Não estou falando de um programa standalone (como dashboard ou coisa assim) e sim uma infraestrutura que inclua rede, banco de dados, pré/pós processamento
	Uma infra que suporte a aplicação que está recebendo deploy, que aguente o fluxo de dados (a frequência de atualização e quantidade de objetos comunicando)

Alto grau de heterogeneidade de dispositivos e protocolos de redes

Desafios:
	- Interoperabilidade e integração dos diversos componentes que fazem parte dos ambiente IoT
	- Escalabilidade desses ambientes
	- Grande volume de dados
	- Gerenciamento de dispositivos

Plataforma é para ser uma solução "fácil" de contornar esse problema
	Mas ainda não está tão maduro
	Suporte a adaptação de aplicações e gerenciamento é um grande mercado

Fazendo uma plataforma própria
	Um sistema que consiga comunicar os dispositivos e então subir uma api para subir uma dashboard para o problema
Quais caixinhas implementar?
Mais de 1k propostas, acaba gerando até plataforma para inter-operar plataformas
Ser independente da rede/comunicação, 
Ter um modo de armazenar os dados (existem bancos para armazenar dados temporais como o influxDb) 
Quero enxergar a rede independente de como ela está fisicamente mas ainda poder operar ela/nela, gerenciar ela, alterar configurações
Como vou autenticar tudo isso (segurança)

WSO2, MANIOT, EcoDIF

Exemplos:
https://thingspeak.mathworks.com/
https://thingsboard.io/
https://cloud.google.com/architecture/connected-devices/iot-platform-product-architecture
https://thinger.io/

