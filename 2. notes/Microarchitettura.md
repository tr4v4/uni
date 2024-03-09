---
tags:
  - category/note
  - status/finished
  - topic/architettura-degli-elaboratori
date: 18-10-2023 11:09:38
links:
  - "[[Lecture 16102023125805]]"
  - "[[Lecture 18102023151217]]"
  - "[[Lecture 19102023130600]]"
---
# Microarchitettura
---
## Introduzione
> E' la microarchitettura che indica alle componenti come realizzare il [[Ciclo di fetch-decode-execute|ciclo di fetch-decode-execute]]. Quindi **la microarchitettura gestisce il flusso dei dati delle singole componenti logiche**[^1].

Ci sono due sistemi di implementazione delle microarchitetture:
- attraverso [[Circuiti combinatori|circuiti combinatori]] (come la [[Microarchitettura HACK|microarchitettura HACK]])
- attraverso la [[Microprogrammazione|microprogrammazione]]

E' per questo motivo che esiste la differenza tra le architetture [[CISC e RISC]].

Ad ogni modo, il flusso dei dati all'interno delle _architetture moderne_ passa attraverso le [[Cache|cache]]. Talvolta addirittura sono previsti algoritmi di [[Paginazione|paginazione]] che consentono di implementare [[Memoria virtuale|memorie virtuali]] che fungono da estensione della RAM _virtualmente_. Sempre nelle architetture più moderne è previsto ormai il [[Pipelining|pipelining]].

## Microarchitetture moderne
Oggigiorno le microarchitetture sfruttano le tecniche sopra descritte, ma in modo sostanzialmente diverso. _Sfruttano al meglio l'hardware che hanno_, facendo le operazioni nell'ordine più comodo ed efficiente per l'architettura della CPU, e **solo dopo si riordinano le parti per avere i risultati corretti**.

E' il caso per esempio della microarchitettura dell'_Inter Core i7_. Questa presenta, tra le varie componenti, l'**unità di ritiro**, un blocco che ha lo scopo di _rendere definitivi i risultati delle istruzioni nell'ordine giusto_.

Si dimostra che questo approccio è più efficiente di quello basato sulla "correzione" continua delle varie istruzioni (con particolare riferimento alle [[Pipelining#Problematiche|problematiche della pipeline]]).

Questa microarchitettura, quindi, si replica per tutti i **core** della CPU:
![[intel-core-i7.png]]

## Referenze
[^1]: vedi [[Macchina multilivello|macchina multilivello]]