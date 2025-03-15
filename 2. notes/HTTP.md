---
tags:
  - category/note
  - status/finished
  - topic/tecnologie-web
  - topic/reti-di-calcolatori
date: 06-11-2024 21:15:59
links:
  - "[[Lecture 10102024151443]]"
  - "[[Lecture 13122024132854]]"
---
# HTTP
---
## Introduzione
> **HTTP** (_HyperText Transfer Protocol_) è un [[Protocollo di rete|protocollo]] di [[Livello applicazione|livello applicativo]], nato principalmente per il trasferimento di pagine [[Web|web]].

## Caratteristiche
Questo protocollo ha le seguenti caratteristiche:
- _client-server_, il client attiva la connessione e richiede dei servizi, mentre il server accetta la connessione;
- _generico_, ossia indipendente dal formato dati con cui vengono trasmesse le [[Risorsa|risorse]];
- _stateless_, quindi il server non è tenuto a mantenere informazioni che persistano tra una connessione e la successiva sulla natura, identità e precedenti richieste di un client.

Nella fattispecie, HTTP si appoggia a [[TCP]]

### Persistenza
L'HTTP, a seconda delle versioni, puo' essere di due categorie:
- **non-persistente** --> viene trasferita una sola risorsa web su una connessione TCP, poi questa viene chiusa; di conseguenza il transito di molte risorse richiede l'apertura e la chiusura di molte connessioni TCP;
	- in questo caso calcoliamo il _response time_ come 2[[RTT]] + tempo di trasmissione del file (il primo RTT per stabilire la connessione TCP, il secondo per richiedere il file);
- **persistente** --> piu' risorse web sono trasferite su una singola connessione TCP;

### Risorse
_Le risorse HTTP sono separate dalla loro rappresentazione_, il che significa che questo protocollo fornisce dei **meccanismi di negoziazione del formato di dati**, e non è dipendente da essi.

## Versioni
L'HTTP si è evoluto nel tempo, passando da una versione all'altra. Le versioni principali sono:
- [[HTTP-2]]
- [[HTTP-3]]

## Referenze
- [[Richiesta HTTP]]
- [[Risposta HTTP]]
- [[Metodi HTTP]]
- [[Cookie]]
- [[HTTP caching]]