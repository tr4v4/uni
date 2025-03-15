---
tags:
  - category/note
  - status/finished
  - topic/ottimizzazione-combinatoria
date: 02-03-2025 16:48:50
links:
  - "[[Lecture 26022025091753]]"
---
# Selezione di sottoinsiemi
---
## Introduzione
> La **selezione di sottoinsiemi** e' una classe di [[Problema di ottimizzazione|problemi di ottimizzazione]] di [[Programmazione lineare intera|programmazione lineare intera]] in cui, dati:
> - $N = \{1, \cdots, n\}$ insieme finito di elementi;
> - $F = \{F_{1}, \cdots, F_{m}\}$ una famiglia di sottoinsiemi di $N$ ($F_{j} \subseteq N$);
> - $c_{j}$ costo associato ad ogni $F_{j}$
> 
> si vuole determinare $D \subseteq F$ di _costo minimo_ che soddisfi certi vincoli.
> Formalmente si rappresenta la situazione come una matrice _costante_ $A$ di variabili logiche $a_{ij} \in \{0, 1\}$, dove $$a_{ij} = \begin{cases} 1 & i \in F_{j} \\ 0 & i \notin F_{j} \end{cases}$$
> Quindi, il vettore delle variabili (logiche) avra' la forma $x = (x_{1}, \cdots, x_{m})$ dove $$x_{j} = \begin{cases} 1 & F_{j} \in D \\ 0 & F_{j} \notin D \end{cases}$$
> mentre la funzione obiettivo da minimizzare sara' semplicemente
> $$\sum\limits_{j=1}^{m} c_{j}x_{j}$$
> I vincoli, invece, dipendono dal tipo di problema:
> - [[Problema di copertura]]
> - [[Problema di partizione]]
> - [[Problema di riempimento]]

## Esempi
### Problema delle commesse
- un'azienda deve decidere come impiegare i suoi $n$ dipendenti $1, \cdots, n$
- l'azienda, nell'intervallo di tempo considerato, deve evadere $m$ commesse $1, \cdots, m$
- ciascuna commessa $j$ DEVE essere svolta dal sottoinsieme $F_{j} \subseteq \{1, \cdots, n\}$ dei dipendenti dell'azienda
- ogni commessa, se evasa, darebbe luogo ad un ricavo pari a $r_{j}$ €
- ogni dipendente può lavorare ad una singola commessa nell'unità di tempo
- soluzione
	- intanto è un problema di selezione di sottoinsiemi
	- $N = \{1, \cdots, n\}$ dipendenti
	- $F = \{F_{1}, \cdots, F_{m}\}$ commesse
	- $a_{ij} = \begin{cases} 1 & i \in F_{j} \\ 0 & i \notin F_{j} \end{cases}$
	- nella fattispecie è un problema di riempimento: non c'è bisogno che ogni dipendente sia assegnato a una commessa, qualcuno può rimanere anche fuori
	- variabili:
		- $x_{j} = \begin{cases} 1 & \text{la commessa j è tra quelle che l'azienda esegue} \\ 0 & \text{altrimenti} \end{cases}$
		- $x_{j} \in \mathbb{N}$
	- vincoli:
		- $0 \leq x_{j} \leq 1 \ \ \ \forall j$
		- $\sum\limits_{j=1}^{m} x_{j}a_{ij} \leq 1 \ \ \ \forall i$
	- funzione obiettivo:
		- $\max{\sum\limits_{j=1}^{m} x_{j}r_{j}}$

## Referenze