---
tags:
  - category/note
  - status/finished
  - topic/ingegneria-del-software
date: 29-09-2025 21:43:51
links:
  - "[[Lecture 29092025103533]]"
  - "[[Lecture 06102025160756]]"
---
# Design di sistemi software
---
## Definizione
> Per **design di sistemi software** (o **system design**) intendiamo il _modo in cui strutturo un sistema software in sottosistemi_.

Per esempio: [[Architettura a micro-servizi|architettura a micro-servizi]], [[MVC]], ecc...

## Contratto
Il design di solito si fa mediante quello che si chiama un **contratto**: l'_insieme di caratteristiche usate per definire cosa sta dentro un sistema, e i vincoli presenti all'interno del sistema_.

## Principi
Per scrivere sistemi software complessi bisogna tenere conto di una serie di principi di _design del software_.

### Moduli e sub-system
Vogliamo differenziare i moduli dai sub-systems:
- _sub-system_
	- fanno una task specifica o un insieme di responsabilita' (approccio procedurale); insieme di classi (approccio [[Linguaggio di programmazione orientato a oggetti|OO]])
	- es.: [[DBMS]]
	- per spezzettare un system in piu' sub-system, nell'approccio orientato agli oggetti, useremo i [[Package|package]]
- _modulo_
	- piu' specifico al linguaggio
	- insieme o libreria di funzioni che fanno una task specifica (approccio procedurale); oppure classi (approccio OO)

### Astrazione e information hiding
L'astrazione, o information hiding, si realizza mediante _interfacce_. In particolare i moduli espongono delle interfacce attraverso le quali è possibile accedervi, senza toccarne l'[[Implementazione|implementazione]].

Se quest'ultima, infatti, cambia, ma l'interfaccia rimane costante, allora il comportamento semantico non cambia: cambiano solo le procedure per ottenere il risultato.

### Low coupling
Vogliamo dividere il **codice in porzioni il meno interdipendenti possibili**. Avere 0-coupling è impossibile... ci sarà sempre un qualche collegamento tra una componente e un'altra. Ma bisogna cercare di _organizzare il codice in parti tra di loro coese, autodipendenti, e che siano il meno connesse possibili con il resto_.

Una dipendenza è per forza necessario, per esempio:
- una funzione/metodo che chiama una funzione/metodo
- accoppiamento di strutture dati
- sottoclassi
	- grande mito: con gerarchie di classi si riducono i costi di produzione
	- si e' scoperto empiricamente invece che la presenza di grandi gerarchie di classi produce una sostanziale incomprensione di quello che succede
		- [[Ereditarietà|ereditarieta']]
		- [[Overriding|funzioni virtuali]] e non virtuali
	- insomma dopo tot. livelli di ereditarieta' il programma diventa illeggibile
	- GO e Rust (pseudo-oggetti) ha abolito l'ereditarieta' per questo
	- Java ha l'ereditarieta' singola! (solo 1 superclasse)
- un modulo fa uso di una feature di un compilatore o di una syscall del sistema operativo --> assolutamente da non fare!

### Alta coesione
Dualmente al low coupling, si richiede un'_alta coesione all'interno di un modulo_.

I livelli crescenti di coesione sono:
- _coincidentale_ - elementi messi insieme senza ragione
- _logica_ - connessione di funzionalita'
- _temporale_ - connessione temporale, certa funzionalita' eseguita subito prima o subito dopo un'altra --> molto usata nei sistemi operativi
- _procedurale_ - legata ai sistemi di [[Segmentazione|memoria segmentata]]
- _comunicazionale_
- _sequenziale_
- _informazionale_
- _funzionale_

Le più importanti sono le ultime due!

### Semplicità
Secondo i vecchi dettami del _design for reuse_, si pensava che il miglior modo per sviluppare software fosse quello di anticipare le funzionalità che sarebbero state richieste in futuro: **sbagliatissimo**! Si rischia così facendo di:
- implementare funzionalità inutili, che non sarebbero e non saranno mai richieste in futuro;
- sprecare tempo;
- _rendere più complesso il codice_.

Invece, si suggerisce particolarmente il **[[Refactoring|refactoring]]**.

Nel particolare, però, a che livello di semplicità ci appoggiamo? Ci sono i 3 seguenti livelli:
- a _livello di metodo_ - piccoli metodi con piccole firme;
- a _livello di modulo_ - piccola interfaccia pubblica;
- a _livello di sistema_
	- evitare moduli "middle-man"
	- poche variabili globali
	- minimizzare le informazioni condivise
	- gerarchie piu' piccole possibili
- a _tutti i livelli_, evitare di duplicare il codice!

## Referenze