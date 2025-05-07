Usa uma bobina para pegar a energia, processar e refletir a frequência com as informações
Tem flag para invalidar, apagar tudo, criptografar
Sempre é leitor - > tag 
Tag só tem um chip de memória e um capacitor em sua maioria

A maioria se baseia em que não terá ninguém utilizando a frequência naquele momento, até porquê a chance de estarem utilizando uma frequência e fazendo a transmissão e leitura em tempos diferentes

Mas para lidar com diversos leitores ao mesmo tempo para evitar a colisão é ListenBeforeTalk 
	O leitor escuta o canal e espera até que esteja vazio, daí espera uma quantidade de tempo e aí sim transmite
	
Para múltiplas tags, se usa QuerySlotProtocol
	O leitor transmite um parâmetro Q, cada etiqueta reseta sua flag, cada etiqueta gera um número Q-bit Aleatório, armazena-o em um contador de slot, quando o contador de slot chega a zero, ele faz o backscattering
	E esse processo se repete
	Q grande -> muitos slots vazios, Q pequeno == muita colisão

