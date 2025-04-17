---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 06-04-2025 17:21:56
links:
  - "[[Lecture 18032025163208]]"
---
# BGP
---
## Introduzione
> Il **BGP** (_Border Gateway Protocol_) è un [[Protocollo di routing|protocollo di routing]] di tipo _path-vector_ utilizzato per il routing tra sistemi autonomi (AS) su Internet. È progettato per gestire la complessità e la scala della rete globale, consentendo agli AS di scambiare informazioni sui percorsi disponibili e le politiche di instradamento.

BGP si compone di:
- _eBGP_ --> per ottenere informazioni di routing tra AS;
- _iBGP_ --> per propagare le informazioni ottenuto da eBGP all'interno di un AS.

## Funzionamento
Fondamentalmente quando un router BGP riceve un'informazione da un router BGP di un altro AS, lo comunica a tutti i router BGP del proprio AS. Quest'informazione arrivera' anche a un altro router BGP dello stesso AS, che la comunica a un router BGP di un altro AS, e cosi' via.

### Messaggi
I messaggi BGP sono di 4 tipi:
- **OPEN** --> per stabilire una connessione tra due router BGP;
- **UPDATE** --> per annunciare nuovi percorsi o rimuovere percorsi esistenti;
- **KEEPALIVE** --> per mantenere viva la connessione tra i router BGP.
- **NOTIFICATION** --> per segnalare errori o condizioni particolari.

## Referenze