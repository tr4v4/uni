---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 14-12-2024 16:39:44
links:
  - "[[Lecture 27112024132652]]"
  - "[[Lecture 29112024132404]]"
---
# Demultiplexing
---
## Introduzione
> Il **demultiplexing**, nell'ambito delle reti, è quel _processo che consente di ricevere più flussi di dati da [[Socket|socket]] differenti su una singola connessione_, sulla falsa riga del [[Demultiplexer|demultiplexer]].

Questo meccanismo viene _implementato al [[Livello trasporto|livello trasporto]] sulla base del numero di [[Porta|porta]] dei [[Segmento|segmenti]]_.

## Modalità
Ci sono diverse modalità per fare demultiplexing, in particolare quello **connectionless** e **connection-oriented**.

### Connectionless
Viene usato in caso di utilizzo del protocollo [[UDP]], e si basa semplicemente sul controllo del numero di porta di destinazione di ogni pacchetto: il pacchetto viene inviato all'applicazione che sta ascoltando su quella porta.

Non dovendo stabilire alcuna connessione, se due client inviano un pacchetto allo stesso socket (applicazione), il tutto viene gestito da una [[Coda|coda]]: _il sistema operativo mette i pacchetti in coda e li invia all'applicazione in ordine di arrivo_.

### Connection-oriented
Viene usato in caso di utilizzo del protocollo [[TCP]], ed è più complesso del precedente. Infatti qui deve stabilirsi una connessione tra mittente e destinatario, e quindi _bisogna tenere traccia di queste connessioni_.

Quello che avviene è che per ogni servizio esposto dal server viene creato un _welcoming socket_, che si occupa di ricevere le richieste di apertura di una connessione TCP ([[Three-way handshake|three-way handshake]]). Una volta che viene stabilita la connessione, **il server istanzia un client socket legato alla connessione con quel preciso client**, chiamato _connection socket_. In questo modo il server può gestire più connessioni su una stessa porta contemporaneamente.

In altri termini, ogni client socket sul server è composto da una **quadrupla** `(indirizzo IP sorgente, porta sorgente, indirizzo IP destinazione, porta destinazione)` che _identifica univocamente la connessione tra quell'applicazione e il client_.

Ogni client socket, infatti, è indipendente ed eseguito parallelamente agli altri. La gestione dei client socket può avvenire:
- _tramite [[Processo|processi]]_ --> ogni client socket è associato ad un processo --> dispendioso in termini di risorse;
- _tramite [[Thread|thread]]_ --> ogni client socket è associato ad un thread --> più efficiente in termini di risorse.

<u>Nota bene</u>: è necessario un buffer, sia di invio (sul client) che di ricezione (sul server), per poter preparare i segmenti da inviare e riordinare i segmenti ricevuti.

## Referenze