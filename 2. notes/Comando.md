---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 16-03-2025 16:43:12
links:
  - "[[Lecture 27022025131944]]"
  - "[[Lecture 05032025111458]]"
---
# Comando
---
## Introduzione
> Un **comando** e' un'_entità sintattica la cui valutazione non necessariamente restituisce un valore, ma può avere un effetto collaterale_ (ossia una modifica dello stato della computazione senza restituzione di un valore, modifica dello store, delle variabili).

## Costrutti
I costrutti principali sono:
- _comando sequenziale_ --> `C1 ; C2`
	- costrutto base dei linguaggi imperativi
	- in alcuni linguaggi il `;` funge da terminatore
- _comando composto_ --> `{ ... }`
	- all'interno del blocco ci possono essere tanti comandi, e questo diventa un comando singolo
- _`GOTO`_
	- molto dibattuto
	- considerato alla fine dannoso, e contrario ai principi della programmazione strutturata (antesignana della programmazione object-oriented)
		- si deve prevedere un solo punto di ingresso e uno solo di uscita
		- togliere il `GOTO` permette di evitare lo _spaghetti code_
- _comando condizionale_
	- sia `if then else` che `case`
	- il `case` è più efficiente, perché a livello di compilazione viene gestito in modo estremamente compatto e veloce --> non si guardano tutti i rami, ma si salta direttamente al ramo giusto
	- ![[case-compilazione.png]]

Altri costrutti fondamentali, senza i quali non otterremmo formalismi di calcolo [[Turing-completezza|Turing-completi]] (ma solo [[Automa a stati finiti|automi a stati finiti]]):
- [[Iterazione]]
- [[Ricorsione]]

## Referenze