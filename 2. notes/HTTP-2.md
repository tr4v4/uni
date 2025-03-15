---
tags:
  - category/note
  - status/finished
  - topic/tecnologie-web
date: 25-11-2024 11:35:03
links:
---
# HTTP-2
---
## Introduzione
> **HTTP-2** è una versione del protocollo [[HTTP]] che è stata sviluppata per migliorare le prestazioni delle applicazioni [[Web|web]].

## Caratteristiche
E' basata su SPDY, un protocollo sviluppato da Google per ridurre i tempi di latenza. Ha introdotto novità importanti quali:
- _multiplexing_, ossia la possibilità di inviare più richieste e risposte su una singola connessione, senza rispettare necessariamente l'ordine di invio;
- _supporto per operazioni push_, che permette al server di inviare al client risorse aggiuntive, potenzialmente richieste in futuro, senza che quest'ultimo le abbia richieste;
- _compressione degli header_, ossia le [[Richiesta HTTP|richieste HTTP]] non sono più inviate in "plaintext", ma sono compresse per ridurre la quantità di dati scambiati tra client e server;

### Algoritmo di compressione
HTTP/2 utilizza l'algoritmo di compressione [[HPACK]] per ridurre la quantità di dati scambiati tra client e server. Per esempio, euristicamente parlando, **se il client produce più richieste simili, l'algoritmo memorizza le informazioni comuni e le invia una sola volta**.
![[hpack.png]]

Il risultato è una _riduzione di circa il 30% degli header scambiati_.

## Referenze