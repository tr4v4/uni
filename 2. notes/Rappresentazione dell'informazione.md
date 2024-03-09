---
tags:
  - category/note
  - status/finished
  - topic/architettura-degli-elaboratori
date: 08-10-2023 18:58:09
links:
  - "[[Lecture 05102023130513]]"
---
# Rappresentazione dell'informazione
---
## Introduzione
Ogni cosa all'interno di un calcolatore è rappresentata sottoforma di **bit**. Ogni immagine, suono, video, testo, carattere, numero è sempre rappresentato nelle due cifre che costituiscono il [[Codice binario|codice binario]]: _0_ e _1_. Come una sequenza di bit è _interpretata_ dalla macchina è un'altra questione[^1], a noi ora interessa studiare delle **codifiche** che consentano di rappresentare qualunque informazione sottoforma di 0 e 1.

In particolare scopriremo che _il computer non può rappresentare ogni numero_, ma a volte solo delle approssimazioni. Ci concentreremo sulla rappresentazione di:
- [[Codifica numeri interi|numeri interi]]
- [[Codifica floating-point|numeri decimali]]
- [[Codifica caratteri|caratteri]]

## Problemi e correzioni
A prescindere dal tipo di dati che si vuole rappresentare, una volta trovato il giusto sistema di codifica/decodifica, rimane il problema della [[Codici correttori|correzione dell'errore]].

## Referenze
[^1]: abbiamo visto che sono le [[Istruzione|istruzioni]] ad interpretare il significato dei dati salvati in [[RAM]]