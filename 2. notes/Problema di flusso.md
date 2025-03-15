---
tags:
  - category/note
  - status/finished
  - topic/ottimizzazione-combinatoria
date: 09-03-2025 18:40:21
links:
  - "[[Lecture 05032025091441]]"
---
# Problema di flusso
---
## Introduzione
> Un **problema di flusso** e' un [[Problema su rete|problema su rete]] in cui la soluzione e' un [[Flusso|flusso]].

## Vincoli
Per modellizzare i problemi di flusso e' sufficiente elencare una serie di vincoli standard:
- _flusso ammissibile_
- _domanda e offerta equivalenti_
- _conservazione del flusso_

### Flusso ammissibile
Si tratta del vincolo piu' semplice, che prevede che per ogni arco il flusso sia compreso tra la sua capacita' inferiore e quella superiore:
$$l_{ij} \leq x_{ij} \leq u_{ij} \ \ \ \ \ \ \forall (i, j) \in A$$

### Domanda e offerta equivalenti
Non si tratta di un vincolo vero e proprio, ma piu' di _un "check" sui parametri_. Si vuole infatti verificare che cio' che entra nella rete equivale a cio' che esce. Espresso in termini dei fattori di sbilanciamento $b_{i}$, si deve avere che
$$\sum\limits_{i \in D} b_{i} = -\sum\limits_{i \in O} b_{i} \ \ \ \iff \ \ \ \sum\limits_{i \in N} b_{i} = 0$$
dove:
- $D = \{i \in N | b_{i} > 0\}$, nodi di domanda (output);
- $O = \{i \in N | b_{i} < 0\}$, nodi di offerta (input).

### Conservazione del flusso
Si vuole in questo ultimo vincolo imporre che per ogni nodo $i \in N$, il flusso in entrata e in uscita deve bilanciarsi. In altre parole, cio' che entra negli archi entranti in $i$, meno cio' che esce dagli archi uscenti da $i$, dev'essere uguale allo sbilanciamento $b_{i}$:
$$\sum\limits_{(j, i) \in BS(i)} x_{ji} - \sum\limits_{(i, j) \in FS(i)} x_{ij} = b_{i} \ \ \ \ \ \ \ \ i \in N$$
dove:
- $BS(i) = \{(k, i) | (k, i) \in A\}$, archi entranti in $i$;
- $FS(i) = \{(i, k) | (i, k) \in A\}$, archi uscenti da $i$.

## Ipotesi semplificative
Solitamente, per semplicita', si impone sempre
$$l_{ij} = 0 \ \ \ \ \forall (i, j) \in A$$
Questa imposizione non diminuisce l'espressivita' dei problemi di flusso. Infatti **e' sempre possibile trasformare un problema con capacita' inferiore nulla in uno con capacita' inferiore non nulla**.

### Dimostrazione
Data una rete $G$, ne possiamo costruire una equivalente $H$ che abbia capacita' inferiori nulle nel seguente modo. Per ogni arco $(i, j) \in A$:
1. si _sottrae_ $l_{ij}$ a $b_{j}$ e a $u_{ij}$;
2. si _aggiunge_ $l_{ij}$ a $b_{i}$;
3. si _aggiunge_ $$\sum\limits_{(i,j) \in A} c_{ij}l_{ij}$$alla funzione obiettivo.

Quindi, ad un flusso $x_{ij}$ in $H$ corrispondera' un flusso $x_{ij} + l_{ij}$ in $G$.

<u>Nota bene</u>: puo' succedere che un nodo di trasferimento non lo sia piu', ma non importa.

## Tipologie
A seconda della funzione obiettivo da massimizzare o minimizzare, i problemi di flusso possono essere:
- [[Problema del flusso di costo minimo|MCF]];
- [[Problema del flusso massimo|MF]].

## Referenze