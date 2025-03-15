---
tags:
  - category/note
  - status/finished
  - topic/ottimizzazione-combinatoria
date: 09-03-2025 19:31:27
links:
  - "[[Lecture 05032025091441]]"
---
# Problema del flusso massimo
---
## Introduzione
> Un **problema del flusso massimo** (**MF**) e' un'istanza del [[Problema di flusso|problema di flusso]] in cui la funzione obiettivo da massimizzare e' _il [[Flusso|flusso]] stesso_.

Formalmente, data una [[Rete|rete]] $G = (N, A)$, e fissati due nodi $s$ (sorgente) e $t$ (destinazione), vogliamo trovare il _massimo_ valore $v$ tale che, se
- $b_{s} = -v$,
- $b_{t} = v$,
- $b_{i} = 0$ per tutti gli altri nodi,

allora esiste un flusso ammissibile (di qualsiasi costo). Di fatto, **non esistono neanche i costi in problemi del flusso massimo**.

## Modellizzazione
Il problema del flusso massimo si modellizza nel seguente modo:
![[mf-modellizzazione.png]]

## Rapporti con MCF
Si tratta in effetti di una restrizione di [[Problema del flusso di costo minimo|MCF]]. Infatti, preso un problema di MF, possiamo estenderlo a un problema di MCF in cui:
- _i costi sono nulli_;
- _gli sbilanciamenti sono tutti nulli_;
- _si aggiunge un arco fittizo da $t$ a $s$ con costo $-1$ e capacita' infinita_.

Per esempio, il problema MF della rete
![[mf.png]]

equivale al problema MCF della rete
![[mf-to-mcf.png]]

Infatti, quell'arco aggiunto
- avendo un costo negativo $-1$ dalla destinazione alla sorgente, si invalida il costo minimo, che diventa $-\infty$;
- avendo capacita' illimitata, consente di trasportare il massimo flusso possibile.

## Algoritmi
Per studiare gli algoritmi risolutivi, e' necessario conoscere la nozione di [[Taglio|taglio]] e di [[Taglio s-t|taglio s-t]].

## Referenze