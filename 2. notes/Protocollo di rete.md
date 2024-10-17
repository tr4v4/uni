---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 08-10-2024 20:14:12
links:
  - "[[Lecture 27092024132110]]"
  - "[[Lecture 02102024131913]]"
---
# Protocollo di rete
---
## Introduzione
> Un **protocollo di rete** è un [[Protocollo|protocollo]] di gestione dei processi di comunicazione all'interno di un sistema [[Rete|rete]]. Si compone di regole [[Sintassi|sintattiche]] e [[Semantica|semantiche]] per la definizione di scambi di messaggi non ambigui. Permettono compatibilità dei dispositivi e dei sistemi conformi allo stesso standard.

## Architettura
Solitamente **i protocolli di rete si suddividono in livelli**, _ognuno dei quali affronta e risolve un problema della comunicazione_.

![[protocollo-di-rete-a-livelli.png]]
I livelli superiori effettuano richieste di servizio al livello inferiore; i livelli inferiori forniscono servizi al livello superiore.

La ragione dietro a questa divisione per livello sta in una **maggiore flessibilità e quindi predisposizione al cambiamento**. Non ha senso creare un unico protocollo di rete _monolitico_, ma più protocolli di livello differenti compatibili tra di loro in modo da **rendere l'intero stack di protocolli modulare**.

Per esempio con un protocollo monolitico, _una modifica hardware delle [[Scheda di rete|schede di rete]] richiederebbe una totale revisione del protocollo_. Invece con uno stack di protocolli _una problematica attuale e futura potrà essere risolto modificando solo qualche protocollo di un livello, lasciando invariato tutto il resto_.

In più la divisione per livelli garantisce [[Information hiding|information hiding]], per cui i livello del livello $n$ non devono preoccuparsi di come sono gestiti i problemi del livello $n-1$.

## Standard
I protocolli di rete standard sono:
- _[[Modello ISO-OSI|modello ISO-OSI]]_ - _de jure_
- [[Modello TCP-IP|modello TCP-IP]] - _de facto_

## Referenze