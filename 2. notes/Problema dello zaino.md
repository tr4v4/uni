---
tags:
  - category/note
  - status/finished
  - topic/algoritmi-e-strutture-dati
date: 21-04-2024 22:51:53
links:
  - "[[Lecture 16042024112039]]"
  - "[[Lecture 17042024113805]]"
---
# Problema dello zaino
---
## Introduzione
> Il **problema dello zaino** (o **knapsack problem**) è uno dei problemi algoritmici più conosciuti, risolto con eleganza dalla [[Tecniche algoritmiche|tecnica algoritmica]] della [[Programmazione dinamica|programmazione dinamica]].

## Descrizione
Avendo un insieme $X = \{1, \cdots, n\}$ di $n$ oggetti, ognuno dei quali ha un peso $p[i]$ e un valore $v[i]$, e disponendo di un contenitore in grado di trasportare al massimo un peso $P$, si vuole determinare un sottoinsieme $Y \subseteq X$ tale che:
- _il peso complessivo degli oggetti in $Y$ sia $\leq P$_
- _il valore complessivo degli oggetti in $Y$ sia il massimo possibile, tra tutti gli insiemi di oggetti che possiamo inserire nel contenitore

Fondamentalmente **vogliamo trovare l'[[Insieme massimale|insieme massimale]] di oggetti rispetto al valore che non sfori il peso massimo consentito**.

## Approcci
### Forza bruta
Andarci di [[Brute force|forza bruta]] ha poco senso: dovremmo considerare ogni sottoinsieme possibile, ovvero l'[[Assioma dell'insieme potenza|insieme delle parti]] di $X$:
$$2^{n}$$
sottoinsiemi.

### Greedy
Si può tentare di ottenere un risultato approssimativo usando un approccio [[Algoritmi greedy|greedy]]. In particolare possiamo, ad ogni passo, _scegliere tra gli oggetti ancora non scelti quello di valore massimo tra tutti quelli che hanno un peso minore o uguale alla capacità residua nello zaino_. Oppure di _scegliere ad ogni passo l'oggetto con valore specifico massimo tra quelli rimanenti che hanno un peso minore o uguale alla capacità residua nello zaino_, dove il valore specifico è definito come `$/kg`.

Entrambi gli algoritmi non forniscono sempre la soluzione ottima.

### Programmazione dinamica
Si dimostra che con questo approccio si ottiene invece la soluzione ottima, ma il vincolo è che **i pesi siano interi**.

Quindi definiamo un sottoproblema $P(i, j)$: _riempire uno zaino di capienza $j$ utilizzando un sottoinsieme di primi $i$ oggetti, in modo da massimizzare il valore degli oggetti usati_.
Ora, le soluzioni $V[i, j]$ (di fatto una [[Matrice|matrice]]) saranno i **valori massimi ottenibili** da un sottoinsieme degli oggetti $i$ con zaino di capacità $j$.

Non ci resta che risolvere in modo efficiente il sottoproblema $P(i, j)$, per cui consideriamo i casi:
- _caso banale $j = 0$_ --> lo zaino ha capienza nulla, per cui $V[i, 0] = 0 \ \ \forall i \in \{1, \cdots, n\}$
- _caso banale $i = 1$_ --> si ha a disposizione solo il 1° oggetto, per cui semplicemente bisogna vedere se ci sta o meno nello zaino di dimensione $j$, e se ci sta mettere in $V[1, j]$ il suo valore $v[1]$, infatti
	- $V[1, j] = v[1]$ se $j \geq p[1]$;
	- $V[1, j] = 0$ se $j < p[1]$;
- _caso induttivo su $i > 1$_ --> si aprono due scenari principali:
	1. $j < p[i]$, quindi l'oggetto $i$-esimo da inserire nello zaino è troppo pesante, allora il bottino massimo che riesco a ottenere è $V[i-1, j]$, ovvero il valore nello zaino senza l'oggetto $i$-esimo
		- $V[i, j] = V[i-1, j]$
	2. $j \geq p[i]$, quindi l'oggetto $i$-esimo eventualmente ci sta nello zaino, allora non ci resta che capire se conviene prenderlo o meno
		- se non lo prendiamo il bottino massimo è sempre $V[i-1, j]$;
			- $V[i, j] = V[i-1, j]$
		- se decidiamo invece di prenderlo allora il bottino sarà sicuramente $v[i]$ sommato al bottino massimo ottenibile con uno zaino di peso $j - p[i]$
			- $V[i, j] = v[i] + V[i-1, j-p[i]]$

Riassumendo si hanno le seguenti formule:
$$\begin{align} V[i, 0] =& 0 \\ V[1, j] =& \begin{cases} v[1] & j \geq p[1] \\ 0 & j < p[1] \end{cases} \\ V[i, j] =& \begin{cases} V[i-1, j] & j < p[i] \\ \max(V[i-1, j], V[i-1, j-p[i]]+v[i]) & j \geq p[i] \end{cases} \end{align}$$

La soluzione si troverà nell'ultima cella in basso a destra, ovvero in $V(n, P)$.

Ma attenzione, **ci rimane da sapere quali oggetti consentono di ottenere il bottino massimo**! Per farlo usiamo una matrice ausiliaria $T$ della stessa grandezza di $V$ che per ogni soluzione $P(i, j)$ salva `True` se quell'oggetto è stato preso e `False` altrimenti. Quindi, partendo dalla cella finale andiamo a ritroso per trovare ogni oggetto nel seguente modo:
- se $T[i, j] = True$ allora quell'oggetto è stato preso, il prossimo si trova in $T[i-1, j-p[i]]$;
- se $T[i, j] = False$ allora quell'oggetto non è stato preso, il prossimo si trova in $T[i-1, j]$;

In ogni caso il costo computazionale dell'algoritmo è
$$T(n) = \Theta(n \cdot P)$$
dove $n$ è il numero di oggetti e $P$ il peso massimo. Questo perché _si deve riempire la tabella $V$ di grandezza $n \cdot P$, e ogni cella si riempie con costo costante_.

## Referenze