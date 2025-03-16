---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 16-03-2025 11:30:59
links:
  - "[[Lecture 26022025111603]]"
---
# Lista libera
---
## Introduzione
> La **lista libera** e' una [[Lista|lista]] che implementa l'[[Heap|heap]].

## Teoria
Anzitutto l'heap viene suddiviso in blocchi di dimensione fissa (e anche limitata), collegati tra di loro in maniera sequenziale dalla lista libera.
![[lista-libera-1.png]]

Quindi:
- quando alloco uno o piu' blocchi contigui dell'heap faccio un `POP`;
- quando dealloco faccio un `PUSH`;

Dopo una serie di allocazioni e deallocazioni, si avra' una lista di blocchi che puntano in ordine non sequenziale:
![[lista-libera-2.png]]

## Implementazione
In realta', la precedente implementazione porta necessariamente a problemi di [[Frammentazione|frammentazione]]. Bisogna gestire la lista libera in maniera intelligente: quello che si fa e' di _considerare inizialmente l'heap come un unico blocco, e poi di dividerlo a seconda delle richieste di allocazione_.

La sequenza di allocazione/deallocazione sarebbe allora la seguente:
1. richiesta di allocazione causa la scelta di un blocco di dimensione opportuna (con [[First fit|first fit]] o [[Best fit|best fit]]);
2. se il blocco scelto è più grande (di almento il doppio del necessario), allora viene diviso in due, e la parte rimanente viene aggiunta alla lista libera;
3. quando un blocco è deallocato viene restituito alla lista libera, e se un blocco adiacente è libero i due blocchi sono fusi in un unico blocco;

Sia che si usi first fit, che best fit, **il costo di allocazione rimane lineare nel numero di blocchi liberi**! Per questa ragione, si preferisce usare le [[Liste libere multiple|liste libere multiple]].

## Referenze