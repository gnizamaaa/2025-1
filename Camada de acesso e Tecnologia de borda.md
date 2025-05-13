A modularização do protocolo OSI//TCP/IP é benéfica exatamente porquê conseguimos mudar implementações sem "deixar a internet quebrar"

**Modelo híbrido**
Aplicação -> Transporte -> Inter-Rede -> Host/Rede -> Enlace de Dados -> Física
Aqui pode ter uma mudança de protocolo no meio, n faz sentido uma lâmpada ter IP mas o hub dela sim

**No IoT**
Camada de aplicação -> Aplicação de Rede -> Camada de percepção (sensoriamento)

Percepção
	Objetos inteligentes, monitoram seu contexto, coletam e processam informações
Rede
	Serviços de gerenciamento, roteamento e identificação
Aplicação
	Prover serviços ao clientes

# Topologias
Estrela -> Router central (gateway) e os dispositivos conectados a ele
Malha -> Todos conectam a todos (um mix dos clientes e gateway ao mesmo tempo)
Linear -> Um conecta ao próximo q conecta ao próximo
	Um gateway que é o conectado a internet e o resto só distribuído, é funcional mas tem problemas principalmente se um nó demonstrar falhas
	Funciona para extensão de cobertura de rede

# Tecnologias
WPAN (zigbee, BLE, Thread//OpenThread)-> WLAN (wifi) -> WNAN (Wi-SUN, 6LoWPAN, 5~10km) -> WWAN (3G/4G/5G, SigFOX,)

## Zigbee (IEEE 802.15.4)
Pode ser usado em estrela, tree-cluster e mesh em WPAN
Baixo consumo, bom para automação residencial, interruptor, lâmpada, brinquedos, sensoriamento
A rede é mais barata e consome menos que o sensoriamento em si na maioria das aplicações
Relativamente barata e funciona razoavelmente bem
Comunicação por modulação e sem muito overhead
	Um rádio bem simplista, sem muita segurança quanto a sniffers por exemplo
Protocolo de roteamento AODV
	Aqui se calcula o vetor distância para os nós apenas quando é necessário, não fica recalculando "toda hora"
A segurança vai ter que ser feita pela camada de aplicação (apesar de alguns módulos mais avançados implementarem uma segurança básica)
	Xbee entrega o roteamento e segurança rápido

Sugestão de projeto: Montar uma topologia para sensoriamento de alguns dados utilizando ZigBee
	Como seria a cobertura, em que locais consigo, se é possível uma malha com partes em diferentes localização

## Bluetooth Low-Energy
Dormir mais do que falar, deixar mais tempo desligado e só acionar para ou mandar um beacon que tá vivo ou mandar algum dado
Bluetooth no 4.0:
	Bluetooth alta velocidade
	BLE -> Um subconjunto do Bluetooth tradicional
Não consegue capturar livremente, há uma segurança principalmente estabelecida no pareamento
Basicamente par a par
Tem o protocolo de descoberta, que anuncia as specs que quer deixar como pública
O Bluetooth normal tem o conceito de active slaves, mas no LE não é definido, sendo o padrão não ter suporte (sendo obrigatório ser par a par nesse caso).
É a solução para wearable pela conveniência de poder conectar ao celular e diversos outros dispositivos

Tempo de ar -> O tempo que está transmitindo e ocupando a frequência para todos.

## Wifi (802.11)

## Sigfox (0G)
Internet celular mas focada em ter cobertura e baixo consumo de energia ao invés de velocidade como o 5G, para ser uma LPWAN
Alguns estacionamentos inteligentes estão utilizando Sigfox 
Veio para suprir a necessidade antes de surgir um padrão de comunicação, a primeira que saiu convencendo todo mundo
	Mas é FECHADO o padrão
Implantaram a antena e depois tem que comprar a implementação, o equipamento

Agora veio a LoRA, LoraWan que é similar mas é aberto

## LoraWan
Tem uma aliança de mais de 500 empresas, chegando em um padrão
Usa frequência sub Ghz (diferente na Europa e América)
Transmissão lenta, de 5000b/s
Cabeçalho de 13 bytes
Gateway (profissional, que se conecta com n dispositivos) é um pouco caro, mas barato para empresa e cliente barato

Tem como usar Lora gateway simples (que só aceita conectar com 1) e fazer uma rede mash

Possui um Spread Factor, um parâmetro de quanto eu quero transmitir a mensagem
Quanto maior maior alcance, maior tempo de ar, maior redundância, maior consumo mas menor taxa de transmissão