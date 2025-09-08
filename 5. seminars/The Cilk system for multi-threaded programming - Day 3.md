---
tags:
  - category/seminar
date: 03-09-2025 09:16:10
lecturer: Matteo Frigo
---
# The Cilk system for multi-threaded programming - Day 3
## Concetti
- implementazione di Cilk
	- l'architettura assunta è shared-memory multiprocessor, senza cache (per semplicità)
	- assunzioni
		- modifichiamo il teorema di Brent in modo da includere l'overhead del work e dello span
		- inoltre assumiamo che il grado di parallelismo sia ben più alto del numero di processori
	- dalle assunzioni ricaviamo il principio _work-first_
		- se c'è un tradeoff tra $c_{1}$ (work overhead) e $c_{\infty}$ (span overhead) allora abbassa il primo --> è più influente per la formula di Brent modificata
		- per minimizzare gli overhead dobbiamo fare (controintuitivamente) più esecuzioni sequenziali che parallele! quindi fare tante serial elisions
	- overhead
		- `spawn` - devo salvare informazioni sulla continuazione del processo che spawna il figlio, in modo che chi ruba il frame padre sa da dove ripartire
			- la versione della funzione dopo la serial elision deve salvare esattamente le stesse informazioni dello stack --> ma lo spawn non ha supporto hardware
		- deque - nella versione parallela devo consentire l'operazione di steal, per muovere un frame da un deque a un altro
			- inoltre lo stack dev'essere allocato
		- outstanding children - dobbiamo fare in modo che il parent sappia se è l'ultimo a fare `sync`
		- conflitto tra steal e `return` - non si può fare return facilmente --> tuo padre potrebbe essere stato rubato
	- strategie
		- **two-clone compilation**
			- ogni funzione viene clonata in una versione _fast_ e in una _slow_
				- fast - parte dall'inizio della funzione e assume che il frame non sia mai stato subato
				- slow - può partire dal mezzo e gestisce outstanding children; uno steal fa partire l'esecuzione dallo slow clone
			- funzionamento
			- la `sync` nei fast-clone è una no-op, per le proprietà dello stesso clone
			- la `sync` nei slow-clone invece è più complesso
				- per farlo si introduce il full frame - mantiene le informazioni sulla gerarchia dei frame
				- gli stack frame invece sono i frame semplici (fast) che mantengono le informazioni sulla funzione e basta
				- nota
					- gli stack frame (fast) introducono work
					- i full frame (`steal`) introducono span (teorema che lega gli steal al critical path)
			- funzionamento
				- il top dello stack è sempre un full frame
				- se viene rubato allora quello sotto viene promosso a full frame - il top deve sempre mantere le informazioni sul parallelismo
			- conflitto worker-thief
				- se una pop e una steal accedono allo stesso frame
				- soluzioni
					- _stealing protocol_
						- lock sulla deque che favorisca i worker --> è in linea con il work-first principle!
						- questo si implementa nello stealing protocol
							- il problema è che il `pop` è piuttosto lungo
					- ma possiamo farlo senza lock?
						- [[Algoritmo di Peterson]]!
						- nella realtà non funziona
							- prima bisogna fare `store` e poi `load` di `A_wants` e `B_wants`
							- ma i processori (non i compilatori eh!) se vedono che non c'è dipendenza tra store e load (non accedono alle stesse variabili) li swappano!
								- per una questione di greedyness degli algoritmi
								- poi i compilatori si sono presi la libertà di farlo al posto dei processori
						- soluzioni
							- si può fare `memory_fence()`, un'istruzione che forza a rispettare l'ordine di load e store
					- ora funzia
						- nella realtà però si può creare starvation sui lock -> un thief può rimanere lì per molto tempo
						- si può fare con `try_lock()` ma a quel punto non è più $O(1)$
					- final stealing protocol

## Domande

## Referenze