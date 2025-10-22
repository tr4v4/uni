---
tags:
  - category/note
  - status/finished
  - topic/ingegneria-del-software
date: 06-10-2025 14:58:12
links:
  - "[[Lecture 06102025105214]]"
  - "[[Lecture 06102025160756]]"
---
# Diagramma delle sequenze
---
## Introduzione
> I **diagrammi delle sequenze** mostrano _come un oggetto interagisce con gli altri oggetti_. Gli oggetti e gli attori sono disposti orizzontalmente, e gli eventi disposti in linee verticali sotto di essi.

![[diagramma-delle-sequenze-1.png]]
![[diagramma-delle-sequenze-2.png]]

Di solito si mettono le istanze, [[Oggetto|oggetti]], e non le [[Classe|classi]]. In particolare si distinguono:
- istanze - oggetti specifici
- lifeline - ruoli, oggetti piu' generici

Esistono dei messaggi di creazione e distruzione degli oggetti. Si possono mettere anche gli stati.
E' possibile racchiudere una parte del diagramma all'interno di un frammento. Questi frammenti possono essere identificati da degli operatori: _loop_, _opt_, _alt_, ecc...

## Azioni
Le azioni sono:
- _sincrone_ - freccia completa, bloccano il chiamante;
- _asincrone_ - freccia a metà, non bloccano il chiamante;

## Referenze
- [[Diagramma delle collaborazioni]]