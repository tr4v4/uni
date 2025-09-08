---
tags:
  - category/seminar
date: 02-09-2025 09:20:55
lecturer: Matteo Frigo
---
# The Cilk system for multi-threaded programming - Day 2
## Concetti
- creiamo lo scheduler per applicare il greedy scheduling
- usiamo un'approssimazione - **CILK work-stealing scheduler**
	- funzionamento
		- ogni processore ha una doubly-ended queue (_deque_), ossia uno stack in cui si accede sia dall'alto che dal basso
		- quando un processore esegue `spawn` pushiamo un nuovo frame nel deque (bottom) e parte l'esecuzione della funzione chiamata
			- nota bene: non ce lo si aspetta! non viene creato alcun thread, né processo
		- quando si esegue `return` si fa pop, esattamente come nello standard
		- quando il deque si svuota parte il parallelismo _randomized work stealing_:
			- il processore prende un frame dal top di una deque random di un altro processore
				- quel frame ovviamente essendo in top non è eseguito
		- quando si esegue `sync` il processore sospende il frame e fa uno steal, se il frame ha dei discendenti ancora da eseguire, altrimenti continua l'esecuzione
			- un frame sospeso non è in alcuna deque!
			- questo risolve il fatto che si possa fare lo steal dal top di un frame che dovrebbe essere fatto quando si finisce di eseguire gli altri frame stackati sopra!
				- _sicuramente dopo un spawn chiamera sync e quindi si metterà in attesa_
			- l'ultimo processore che fa return di una sync pusha il frame sospeso nella deque
	- analisi
		- spazio
			- _serial elision_ - rimuovi `cilk`, `spawn` e `sync` e da un programma CILK ottieni un programma C
			- teorema: $S_{1}$ è la quantità di spazio di stack di una serial elision e $S_{P}$ lo spazio di stack in un'esecuzione con $P$ processori, allora $$S_{P} \leq P S_{1}$$
				- dimostrazione, bisogna introdurre concetti per gestire i frame sospesi
					- _busy frame_ - se un processore ci sta lavorando
					- busy-leaves lemma: ad ogni istante di tempo, per ogni frame $F$, o $F$ è busy oppure un suo qualche discendente lo è
					- dimostrazione teorema
			- da un esempio di un bad scheduling capiamo che è necessario partire immediatamente ad eseguire il figlio spawnato per mantenere il bound sullo spazio
		- tempo - difficile
			- teorema: usando randomized work-stealing, si ha (dal teorema di Brent) $$T_{P} \leq \frac{T_{1}}{P} + O(T_{\infty})$$ con alta probabilità (perché è uno scheduler nondeterministico)
				- dimostrazione
					- "lemma" (almost true): se rubo un top frame da tutte le deque riduco lo span di 1
						- relazione tra l'essere nel top di una deque e nell'appartenere a un critical path, non ovvia
					- "lemma" (false but fixable): sopo $\Theta(P)$ steal, con alta probabilità, abbiamo rubato da tutte le deque almeno una volta
					- vogliamo cercare di dire che se sei in alto nella deque allora sei nella critical path
						- per farlo cambiamo il DAG (barando)
						- in questo caso il primo lemma funziona
- fighissimo esempio che mostra il ruolo dello span --> il parallelismo è boundato dallo span del programma!

## Domande
- la scelta nell'algoritmo di work-stealing è randomizzata ma solo tra i processori che hanno almeno due frame nella deque?

## Referenze