---
tags:
  - category/note
  - status/finished
  - topic/algoritmi-e-strutture-dati
date: 19-04-2024 12:21:51
links:
  - "[[Lecture 15042024091754]]"
---
# Shortest Job First
---
## Funzionamento
Si sceglie di **eseguire il processo con tempo di esecuzione minore per minimizzare complessivamente il tempo di attesa di tutti i processi**, implementando a tutti gli effetti un [[Algoritmi greedy|algoritmo greedy]].

Si considerino in particolare $n$ _job_ $p_{1}, \cdots, p_{n}$, ognuno dei quali $p_{i}$ ha un tempo di esecuzione $t[i]$. Per minimizzare il tempo medio di attesa è sufficiente eseguire i job in ordine crescente di tempo di esecuzione.

### Dimostrazione di ottimalità
Consideriamo [[Regole di inferenza del RAA|per assurdo]] una _soluzione ottimale non greedy_ che eseguo un job lungo $A$ prima di uno più corto $B$. Scambiando $A$ con $B$ otteniamo una soluzione con un tempo medio di attesa migliore, ovvero un ottimo globale, in contrasto con l'assunzione iniziale della soluzione ottimale.

**Qed**.

## Referenze