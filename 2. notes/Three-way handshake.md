---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 14-12-2024 16:01:46
links:
  - "[[Lecture 27112024132652]]"
---
# Three-way handshake
---
## Introduzione
> Il **three-way handshake** è un meccanismo di _inizializzazione di una connessione [[TCP]]_ tra due dispositivi. Consiste in una serie di 3 messaggi scambiati tra il mittente e il destinatario per _stabilire una connessione affidabile_ ([[Servizio orientato alla connessione|connection-oriented]]).

<u>Nota bene</u>: gran parte deli servizi di [[Livello applicazione|livello applicativo]] basati su TCP non mantengono aperte le connessioni per la durata dello scambio dei file, ma le aprono e le chiudono ad ogni trasferimento. In questo caso si dice che il protocollo applicativo _non è persistente_.

## Referenze