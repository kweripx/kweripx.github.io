---
title: "The Last Algorithms Course You'll Need"
date: 2023-11-09T03:09:43-03:00
draft: true
tags: 
  - Algorithms
---

Recentemente comecei a acompanhar os vídeos e algumas stream do ThePrimeagen e por conta disso me deparei com o curso gratuito dele, intitulado "**The Last Algorithms Course You'll Need**".
Como um graduado em Ciência da Computação essa é uma matéria que tive já tem algum tempo, então porquê não revisita-la e reaprender conceitos base?
Nesse post irei compartilhar o quê aprendi com o conteúdo apresentado com base nas minhas anotações feitas durante as aulas, junto de alguns snippets de códigos.


## Big O Time Complexity

Big O é uma forma para categorizar os requisitos de tempo ou memoria de seus algoritmos baseado no input. Não busca pretender ser uma forma exata para mensurar. Apenas vai dizer quantos ciclos irá levar, busca dizer de forma generalizada o crescimento do seu algoritmo.

### Exemplo
Quando alguem diz O(n), quer dizer que seu algoritmo vai crescer de forma linear baseado no input. 

Sua utilização tem o intuito de auxiliar na tomada de decisão sobre qual estrutura de dado e algoritmo utilizar. Saber como seu código vai performar torna-se de grande ajuda para criar um bom programa. 

```
function sum_char_codes(n: string): number {
	let sum = 0;
	for (let i = o: i < n.length; ++i) {
		sum += n.charCodeAt(i);
	}
	return sum;
}
```

### Conceitos importantes
1. O crescimento está atrelado ao input. 
2. Constantes são descartadas
	O(2n) --> O(n). Isso porque Big O buscar descrever o crescimento do algoritmo, assim constantes eventualmente se tornam irrelevantes. 
	![[Pasted image 20231109025509.png]]
3. Constantes na prática são importantes, porém nesse caso não se fazem necessárias, sendo assim teoricamente O(100n) é mais rápido que O(n^2).
4. O pior cenário geralmente é a forma que mensuramos.

O snippet acima é de uma complexidade O(n), ou seja, o tempo de execução do programa cresce de forma linear, caso a string que for percorrida aumente seu tamanho em 50%, o tempo de execução do código ira aumentar em 50%.
A forma mais fácil de identificar a complexidade de um código é buscar por loops.

### Complexidades comuns
![[Pasted image 20231109025945.png]]

**O(N^2 )**
```
function sum_char_codes(n: string): number {
	let sum = 0;
	for (let i = 0; i < n.length; ++i) {
		for (let j = 0; j < n.length; ++j) {
			sum += charCode;
		}
	}
	return sum;
}
```
**O(N^3)**
```
function sum_char_codes(n: string): number {
	let sum = 0;
	for (let i = 0; i < n.length; ++i) {
		for (let j = 0; j < n.length; ++j) {
			for (let k = 0; k < n.length; ++k) {
				sum += charCode;
			}
		}
	}
	return sum;
}
```
**O(n log n)**
* Quicksort.
**O(log n)**
* Binary search trees.