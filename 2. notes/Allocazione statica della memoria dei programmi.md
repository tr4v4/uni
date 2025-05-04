---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 25-02-2025 11:16:07
links:
  - "[[Lecture 20022025131602]]"
---
# Allocazione statica della memoria dei programmi
---
## Introduzione
> Per **allocazione statica della memoria dei programmi** si intende il meccanismo di allocazione della [[Memorie|memoria]] per il quale questa viene allocata a _compile-time_.

## Funzionamento
Ad **ogni oggetto viene assegnato un indirizzo assoluto** che e' **mantenuto per tutta l'esecuzione del programma**. Solitamente si allocano staticamente:
- _variabili globali_
- _variabili locali delle funzioni_
- _costanti determinabili a compile-time_
- _tabelle usate dal supporto run-time_ (per [[Type checking|type checking]], [[Garbage collection|garbage collection]], ecc...)

Piu' in dettaglio, **si va a vedere quante funzioni ci sono e per ognuna di esse si alloca lo spazio necessario sulla base di quanto occupa**. Significa che non posso avere la stessa funzione in esecuzione piu' volte contemporaneamente: di conseguenza **la [[Ricorsione|ricorsione]] e' impossibile con la sola allocazione statica della memoria**. Infatti _puo' esistere un unico [[Record di attivazione|record di attivazione]] per la stessa funzione_, e _la chiamata ricorsiva andrebbe a sovrascrivere i dati calcolati dall'istanza precedente_ (come il _valore di ritorno_).

<u>Nota bene</u>: inoltre, **sapere quante chiamate ricorsive saranno eseguite da una funzione ricorsiva e' un [[Problema indecidibile|problema indecidibile]]**.

## Referenze