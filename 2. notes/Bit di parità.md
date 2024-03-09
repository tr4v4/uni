---
tags:
  - category/note
  - status/finished
  - topic/architettura-degli-elaboratori
date: 12-10-2023 22:47:06
links:
  - "[[Lecture 11102023151203]]"
---
# Bit di parità
---
## Introduzione
> La tecnica del **bit di parità** è il più semplice [[Codici correttori|codice correttore]] che consente di rilevare, con 1 solo bit di controllo, un errore dei dati.

## Funzionamento
Fondamentalmente per qualunque parola del codice viene aggiunto 1 bit in più che:
- vale 0 se il numero di bit a 1 della parola è pari
- vale 1 se il numero di bit a 1 della parola è dispari

In questo modo qualunque parola ricevuta in ingresso se ha un numero di bit a 1 dispari sappiamo che è sbagliata.

La [[Distanza di Hamming|distanza di Hamming del codice]] è di 2: per qualunque numero di bit $m$, la parola valida più vicina ad una qualsiasi altra parola valida non può essere distante 1 (_invaliderebbe il bit di parità_); se è distante 2 allora torna ad avere un numero di bit a 1 pari, quindi è la distanza minima.

## Referenze