---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 28-09-2025 15:48:19
links:
  - "[[Lecture 16042025110927]]"
---
# Inferenza di tipo
---
## Introduzione
> L'**inferenza di tipo** e' quel procedimento eseguito dal _type checker_ per inferire il tipo di un'[[Espressione|espressione]]. In particolare, _a partire dalle foglie dell'[[Albero di derivazione|albero di derivazione]] costruito dal [[Parser|parser]], presumibilmente [[Variabile|variabili]] di cui quindi si conosce il [[Tipi di dato|tipo]], si ricava il tipo dell'intera espressione_.

L'_algoritmo di inferenza non riesce sempre a inferire direttamente il tipo di un'espressione_: in tal caso lo mantiene "aperto", procede con l'analisi di altre parti del programma, e in un secondo momento torna sull'espressione con delle informazioni raccolte in piu'.
Se invece nonostante le informazioni raccolte _non e' in grado di inferire il tipo, allora lo segnala all'utente_.

## Funzionamento
Nella fattispecie, _interrompere l'inferenza dell'espressione significa assegnare ad essa una variabile di tipo_, che con l'esplorazione dell'albero di parsing, _arricchisce di vincoli_ --> questo **finche' non rimane che un solo tipo assegnabile all'espressione**.

Per esempio, se ad un'espressione non ancora inferita sara' applicato l'operatore `+`, allora possiamo restringere i tipi possibili di quell'espressione a quelli compatibili con la somma.

L'algoritmo che implementa questa logica si chiama [[Algoritmo di unificazione|algoritmo di unificazione]].

## Referenze