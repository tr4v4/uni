---
tags:
  - category/seminar
date: 01-09-2025 16:31:07
lecturer: Fred B. Schneider
---
# Laws for Cybersecurity
## Concetti
- triangolo CIA effettivamente fa schifo:
	- non è una definizione rigorosa
	- le proprietà non sono ortogonali
- meccanismo di difesa: in realtà la cybersecurity è un mezzo per rilocare di cosa ci fidiamo, e non per proteggere un sistema
- acl e capabilities
	- can $A$ perform $op$ on $Obj$? Undecidable (proved)
- reference monitor
	- non sono universali --> safety property --> può essere visto come un automa a stati finiti! (è un teorema)
	- simulano un automa da inserire prima di ogni riga di un codice, che controlla se l'operazione è accettata o no, e se sì va avanti altrimenti ferma tutto
		- l'automa viene creato sulla base delle policy
		- poi compresso per occupare meno righe di codice possibile
		- questo meccanismo si trova dentro Java
	- PCC - Proof Carrying Code
		- è un proof checker
		- si usa perché: l'automa se il programma è corretto si ottimizza così tanto che non ci sono più righe inserite nel codice in input --> ma uno deve fidarsi che effettivamente si siano cancellate le righe
- monoculture
	- quando tanti sistemi diversi usano lo stesso software per alcuni o tutti i componenti
	- puoi fare:
		- perfection --> crei programmi No Flaws
		- diversity --> nessun attacco rompe tutto
			- puoi fare artificial diversity --> program obfuscation
			- ossia da un programma si ottiene il morph, cambiando le parole con cose random...
			- non possiamo capire quanto sia buona questa tecnica, ma possiamo confrontarla con altre tecniche di difesa
				- type checking! usato come metodo di difesa però
					- statico o dinamico, guarda se tutte le esecuzioni rispettano certe proprietà
				- ma c'è probabilistic dynamic type checking
					- si potrebbe dimostrare che obfuscation e probabilistic dynamic type checking difendono dagli stessi attacchi
					- questo vuol dire che: _un programma in C offuscato e un programma in Java (strongly type checked) sono equivalenti in termini di difesa_!

## Domande

## Referenze