
* **Redes Abertas
* **Redes Fechadas

## Redes Abertas

Uma rede aberta possui chegada e saída para o exterior. Isso está muito vinculado com qual barreira é definida para limitar a rede. **Tudo que chega do exterior precisa OBRIGATORIAMENTE sair, caso contrário o sistema "explode".

![[Pasted image 20250505093500.png]]

![[Pasted image 20250505093326.png]]

Onde,
	r_i = chegada do exterior no servidor i.
	P_ij = Probabilidade de um trabalho recém atendido  no servidor *i* ir para o servidor *j*.

Pergunta:
**Quais são os valores de λ_i?

	λ_1 = r_1 + P_3,1 * λ_3
	λ_2 = r_2 + P_1,2 * λ_1
	λ_3 = r_3 + P_1,3 * λ_1 + P_4,3 * λ_4
	λ_4 = P_2,4 * λ_2 + P_3,4 * λ_3
	r_1 + r_2 + r_3 = P_3,out * λ_3


### * Outra métrica de desempenho

![[Pasted image 20250505094608.png]]

* **Throughput (Vazão) :** Vazão para sistema aberto, não depende da razão de serviço, ***apenas da razão de chegada***.

