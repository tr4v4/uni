---
tags:
  - category/note
  - status/finished
  - topic/ottimizzazione-combinatoria
date: 09-03-2025 19:02:03
links:
  - "[[Lecture 05032025091441]]"
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

## Referenze

[^1]: ricorda un po' la dimostrazione dell'[[Equivalenza tra NFA ed espressioni regolari|equivalenza tra NFA ed espressioni regolari]]!
