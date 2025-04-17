---
tags:
  - category/note
  - status/finished
  - topic/ottimizzazione-combinatoria
date: 09-03-2025 19:02:03
links:
  - "[[Lecture 05032025091441]]"
  - "[[Lecture 19032025092241]]"
---
# Problema del flusso di costo minimo
---
## Introduzione
> Un **problema del flusso di costo minimo** (**MCF**) e' un'istanza del [[Problema di flusso|problema di flusso]] in cui la funzione obiettivo da minimizzare e' il _costo del flusso_.

Si assume che le capacita' inferiori $l_{ij}$ siano nulle.

## Modellizzazione
La funzione obiettivo e'
$$\min cx$$
e in vincoli sono
$$0 \leq x \leq u \ \ \ \ \ \ \ Ex = b$$
dove:
- $c \in \mathbb{R}^{|A|}$ e' il vettore dei costi;
- $u \in \mathbb{R}^{|A|}$ e' il vettore delle capacita' (superiori);
- $E \in \mathbb{R}^{|N| \times |A|}$ e' una sorta di [[Matrice di adiacenza|matrice di adiacenza]] tra nodi e archi (per ogni nodo si guardano gli archi, e negli archi entranti si mette $1$ mentre in quelli uscenti $-1$, e si ottiene il vincolo della conservazione del flusso);
- $b \in \mathbb{R}^{|N|}$ è il vettore degli sbilanciamenti.

## Assunzioni
### Singola sorgente e singolo pozzo
Conviene assumere che ci sia una sola sorgente (nodo di input) e un solo pozzo (nodo di output). E si dimostra che **ogni problema MFC puo' essere trasformato in un problema equivalente con una sola sorgente e un solo pozzo**: e' **sufficiente aggiungere due nodi fittizzi, una sorgente e un pozzo**, tali che
- _al nodo sorgente si attaccano tutte le sorgenti della rete di partenza, collegandoli con archi di costo nullo e capacità superiore pari all'inverso dello sbilanciamento delle sorgenti_;
- _al nodo pozzo si attaccano tutti i pozzi della rete di partenza, collegandoli con archi di costo nullo e capacità superiore pari all'inverso dello sbilanciamento dei pozzi_.

![[mcf-assunzioni-1.png]]
![[mcf-assunzioni-2.png]]
[^1]

### Capacita' dei nodi
A volte **e' utile imporre che anche i nodi abbiano delle capacita'**, ovvero che solo una quantità di flusso compresa nell'intervallo chiuso $[l_{i}, u_{i}]$ possa passare per il nodo $i \in N$. E' possibile modellizzare questa situazione sdoppiando ciascun ndo $i$ in due nodi $i', i''$ tali che
- _tutti gli archi entranti in $i$ vadano a finire in $i'$_;
- _tutti gli archi uscenti da $i$ partano da $i''$_;
- _vi sia un arco fittizio $(i', i'')$ con costo nullo, capacità inferiore $l_{i}$ e capacità superiore $u_{i}$_.

![[mcf-assunzioni-3.png]]

## Preliminari
### Pseudoflusso
Bisogna introdurre la nozione di **pseudoflusso**: è una definizione più lasca di flusso ammissibile, in cui rimane il vincolo sulle capacità, ma i vincoli di sbilanciamento non sono tenuti in conto. Matematicamente deve valere
$$0 \leq x_{ij} \leq u_{ij} \ \ \ \ \forall (i, j) \in A$$
ma definiamo sbilanciamento $e_{x}(i)$ lo sbilanciamento in ogni nodo $i$ della quantità entrante rispetto a quell'uscente nel flusso $x$:
$$e_{x}(i) = \sum\limits_{(j, i) \in BS(i)} x_{ji} - \sum\limits_{(i, j) \in FS(i)} x_{ij} - b_{i}$$

Quindi raccogliamo i nodi sbilanciati nei due insiemi:
- $O_{x} = \{i \in N | e_{x}(i) > 0\}$ --> vogliamo portare via del flusso da un nodo appartenente a questo insieme;
- $D_{x} = \{i \in N | e_{x}(i) < 0\}$ --> vogliamo portare del flusso verso un nodo appartenente a questo insieme.

Ovviamente, se $O_{x} = D_{x} = \varnothing$, allora $x$ è un flusso. Lo sbilanciamento complessivo di uno pseudoflusso $x$ è dato da
$$g(x) = \sum\limits_{i \in O_{x}}e_{x}(i) = - \sum\limits_{j \in D_{x}}e_{x}(j)$$

<u>Nota bene</u>: la seconda uguaglianza deve avvenire, fondamentalmente significa che lo sbilanciamento complessivo dei nodi che offrono flusso dev'essere lo stesso dei nodi che domandano flusso.

A questo punto possiamo generalizzare la nozione di [[Grafo residuo|grafo residuo]] al problema del flusso di costo minimo: è sufficiente che ogni arco comprenda anche un costo! Costruiamo sempre $G_{x}$ con archi concordi e discordi, ma comprendendo ora anche il loro costo. In particolare:
- in un arco concorde $(i, j)$ di $G_{x}$, il costo è semplicemente $c_{ij}$;
- in un arco discorde $(j, i)$ di $G_{x}$, il costo è invece $−c_{ij}$.

Sappiamo che dato un [[Cammino aumentante|cammino aumentante]] $P$, è possibile inviare $0 \leq \theta \leq \theta(P, x)$ unità di flusso lungo $P$, attraverso l'operatore $x(P, \theta)$. Quest'ultimo, nel contesto dei problemi del flusso di costo minimo, sarà indicato come $x \oplus P \theta$.

Quindi, la nozione stessa di cammino aumentante, adesso, avrà un costo:
$$c(P) = \sum\limits_{(i, j) \in P^{+}} c_{ij} - \sum\limits_{(i, j) \in P^{-}} c_{ij}$$

Si verifica che
$$c \cdot (x(P, \theta)) = c \cdot (x \oplus P \theta) = c \cdot x + \theta c(P)$$

### Pseudoflusso minimale
A differenza dei problemi di flusso massimo, non possiamo aumentare il flusso indiscriminatamente: questo costa a seconda di dove passa. Per questo si introduce la nozione di **pseudoflusso minimale**: è uno _pseudoflusso $x$ che ha costo minimo tra tutti gli pseudoflussi con lo stesso vettore di sbilanciamento $e_{x}$_.

## Algoritmi
Gli algoritmi risolutivi sono:
- [[Algoritmo dei cammini minimi successivi]]

## Referenze

[^1]: ricorda un po' la dimostrazione dell'[[Equivalenza tra NFA ed espressioni regolari|equivalenza tra NFA ed espressioni regolari]]!
