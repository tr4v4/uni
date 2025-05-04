---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 02-04-2025 00:25:04
links:
  - "[[Lecture 05032025111458]]"
---
# Ricorsione in coda
---
## Introduzione
> Una [[Funzione informatica|funzione]] `f` si dice di **ricorsione in coda** se contiene solo "_chiamate in coda_", ovvero se restituisce il valore della chiamata di `f'` (in `f`) senza ulteriore computazione.

IN tal caso non è necessaria alcuna [[Allocazione dinamica della memoria dei programmi|allocazione dinamica della memoria]]: è sufficiente un solo [[Record di attivazione|record di attivazione]]!

## Esempio
Prendiamo la funzione ricorsiva che calcola il [[Fattoriale|fattoriale]]:
![[fattoriale.png]]

La sua versione con ricorsione in coda è
![[fattoriale-ricorsione-in-coda.png]]

## Referenze