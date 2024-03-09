---
tags:
  - category/note
  - status/finished
  - topic/architettura-degli-elaboratori
date: 24-11-2023 17:17:21
links:
  - "[[Lecture 20112023130829]]"
---
# Frammentazione esterna
---
## Introduzione
> La **frammentazione esterna** è una [[Frammentazione|frammentazione]] della [[RAM]] che si verifica come conseguenza della [[Segmentazione|segmentazione]].

Lo _swap_ di un segmento dalla memoria secondaria a quella principale non avviene in maniera così banale come per la [[Paginazione|paginazione]]. Questo perché i segmenti hanno grandezze distinte. In particolare la frammentazione esterna si verifica quando **un blocco di una certa dimensione viene sostituito da uno di dimensione minore**, lasciando in memoria un piccolo _gap_ che non è riempibile con nessun altro segmento.

Questi gap, sparsi nella memoria, finiscono con l'accumularsi, portando ad una situazione di stallo, in cui _gli spazi rimasti non sono abbastanza grandi da contenere un nuovo segmento_.

## Soluzione
Per risolvere, o almeno limitare il più possibile la frammentazione esterna, ci sono tre tecniche:
- [[Best fit|best fit]]
- [[First fit|first fit]]
- [[Defrag|defrag]]

Il metodo però migliore per evitare del tutto la frammentazione esterna consiste nel [[Combinazione segmentazione-paginazione|combinare la segmentazione con la paginazione]].

## Referenze