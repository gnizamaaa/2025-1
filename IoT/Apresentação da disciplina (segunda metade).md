Esp8266 -> SoC muito comum

1999 - Primeira menção, muito ligada ao uso de RFID
1991 - Tem um paper científico que dá uma proposta de uma casa inteligente
	 [Paper aqui](https://www.ics.uci.edu/~corps/phaseii/Weiser-Computer21stCentury-SciAm.pdf)
	 Computação em todo lugar em todo momento, computação ubíqua
Até aqui sempre as idéias eram ligadas a rede de sensores e monitores
Temos aqui a ideia de tecnologia em malha, mash
	Temos alguns pontos conectados a rede principal e os outros se organizam retransmitindo e utilizando a rede
	Alguns dos pontos, os mais adequados, irão atuar além de consumidor, como repetidor. Enquanto os mais simples como lâmpadas apenas irão consumir da rede.


## Blocos básicos
Identificação - RFID, NFC, IP
Sensor/atuador - Sensor de temperatura, relé
Processamento - 
Comunicação - Bluetooth, Zigbee, RFID, NFC
	Geralmente tem curto alcance, baixo consumo energético e alta taxa de perdas de mensagens
	Ao menos um canal de comunicação
Dados - Semântica, Conhecimento - Como vou armazenar 
Serviço - Serviços de identificação (mapeamento entre entidades físicas)

## Avaliação
Leitura de artigos, trabalhos práticos, semântica e projeto
Pode abstrair de que os dados já foram coletados para o projeto

# Escolhendo os dispositivos
## Arquitetura básica dos dispositivos
Unidades de processamento/memória otimizadas para economia de energia
Arquitetura RISC -> ARM
FeRAM vs Flash -> FeRAM menor consumo e tempo de escrita. Flash maior capacidade e menor preço
SRAM vs DRAM -> SRAM atualização periódica mais rápida e cara. DRAM maior capacidade.

Não devemos superdimensionar (consumo de energia vai subir) ou subdimensionar (vai travar ou incapacitar do projeto funcionar)

Fontes de energia

Sensores geralmente capturam grandezas físicas de modo analógico, com isso podemos inferir e criar sensores virtuais a partir de vários sensores


