---
tags:
  - category/note
  - status/finished
  - topic/sistemi-operativi
date: 04-05-2025 17:14:45
links:
  - "[[Lecture 04042025092728]]"
---
# Trashing
---
## Introduzione
> Un [[Processo|processo]] (o un intero sistema) si dice in **trashing** quando spende piu' tempo per la [[Paginazione|paginazione]], e in particolare a gestire le [[Page fault|page fault]] attraverso degli [[Algoritmi di paginazione|algoritmi di paginazione]], piuttosto che per eseguire le istruzioni del programma.

## Cause
Tra le piu' problematiche cause di trashing ritroviamo l'_[[Allocazione#Memoria virtuale|allocazione globale]]_: i processi tentano di rubarsi i frame a vicenda, per cui _non si riescono a tenere in memoria i frame utili a breve termine perche' altri processi richiederanno frame liberi_, con il risultato di ricevere page fault ogni pochi passi di avanzamento.

Quello che avviene, nella fattispecie, e' che se capita che molti processi vadano in page fault, la ready queue si riduca; questo induce il sistema ad accettare nuovi processi, che a loro volta andranno in page fault, generando una reazione a catena che blocca completamente il sistema.

![[trashing.png]]

## Soluzioni
Per evitare il trashing, si utilizza il meccanismo del [[Working set|working set]].

## Referenze