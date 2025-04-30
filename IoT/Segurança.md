Frameworks p seguranças de embarcados tendem a ser diferentes 
IoT é pervasivo, está em todo lugar em todo tempo
	Tem muitos dados sensíveis de saúde, uso, localização, hábitos de compra, direção, mídia
Muitos grupos de objetos conectados, com muitos sensores
	Sua segurança é tão forte quanto o elo mais fraco da rede

Uma estratégia simples e trivial é fazer uma rede isolada apenas para IoT
Ninguém vai atualizar a lampada mas o fabricante pode fazer um sistema que eventualmente faça uma checagem para fazer um update OTA
	Há o risco de brickar, resultado de algum erro durante a atualização
	
No IOT como vão ter muitas comunicações de rádio simples broadcast ex.:Zigbee, é um problema considerável o uso de sniffers, Man in the Middle

Software Attacks -> mais perigosos que vão permitir você interromper o serviço daquele aparelho por exemplo
	SQL injection
	Buffer Overflow

## Não linearidade do processamento para monitoramento
Quanto menos poderoso é um dispositivo, maior é, proporcionalmente, o gasto para se monitorar e manter a segurança
	Mesmo sendo o mesmo programa rodando em um PC e um Raspberry PI, o uso do RPI fazendo essa tarefa vai ocupar muito mais do processamento disponível
Devemos combinar vários mecanismos de defesa, trabalhar em diversos níveis do sistema e proteção contra diversos tipos de ataques.
Foco sempre em defender contra ataques de rede e alguns ataques de software com base na instalação remota de malware
Vai chegar um ponto que o tradeoff entre o quanto protegido e o quanto eficiente consigo fazer a tarefa vai nos limitar, vai ficar com um overhead muito grande para algo "simples"
## Primitivas
- Autenticidade
- Integridade
- Confidencialidade

