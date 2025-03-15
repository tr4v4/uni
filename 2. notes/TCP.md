---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 14-12-2024 15:34:52
links:
  - "[[Lecture 27112024132652]]"
  - "[[Lecture 29112024132404]]"
---
# TCP
---
## Introduzione
> Il **TCP** (_Transmission Control Protocol_) è un protocollo di [[Livello trasporto|livello trasporto]] che si occupa della _gestione della corretta consegna dei dati tra due dispositivi_.

Si tratta a tutti gli effetti dello standard architetturale di internet: non per niente il modello "de facto" è lo [[Modello TCP-IP|stack TCP-IP]].

## Caratteristiche
Tra le caratteristiche più importanti ricordiamo:
- è un **servizio di trasporto affidabile**, di tipo [[Servizio orientato alla connessione|connection-oriented]] --> attraverso il [[Three-way handshake|three-way handshake]], la _numerazione dei pacchetti_ e i pacchetti _ACK_;
- applica **[[Controllo della congestione|controllo della congestione]] e [[Controllo del flusso|controllo del flusso]]** --> attraverso il [[Sliding window|meccanismo di finestra scorrevole]];
- implementa l'**associazione tra [[Indirizzo IP|indirizzo IP]] e [[Porta |porta]]** --> attraverso il [[Socket|socket]].

In poche parole, l'[[IP]] di [[Livello rete|livello rete]] non è affidabile (_best effort_) in quanto non garantisce l'ordine di ricezione dei pacchetti corretto né si preoccupa di ritrasmettere quelli perduti: **il TCP è il protocollo che si occupa di ripristinare l'ordine dei pacchetti e di rinviarli in caso di perdita**! E' lui che rende l'effettiva _trasmissione di dati affidabile sul protocollo IP_.

## Criticità
Il TCP presenta alcune criticità, in merito ad attacchi di tipo [[DoS]] e gestione delle sessioni.

### DoS
Se il client non chiude più la connessione TCP, una volta aperta, questa rimane inattiva ma presente sul server. Vale a dire che _occupa risorse server-side che potrebbero essere liberate per dare spazio a nuove connessioni_.

Se tanti client aprono connessioni e non le chiudono, il server si trova a gestire un numero eccessivo di connessioni inattive, _rischiando di andare in crash_.

### Sessioni
Se per qualche ragione la connessione TCP viene interrotta a metà del trasferimento dei dati (magari per un cambio di rete da parte del client), non c'è modo di mantenere traccia della sessione. Questo significa che _non è possibile riprendere il trasferimento dei dati da dove si era interrotto_.

Si pensava che il livello sessione potesse risolvere queste problematiche, ma non è stato così: _ci pensa il [[Livello applicazione|livello applicazione]] a gestire la sessione_.

## Referenze