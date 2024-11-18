---
tags:
  - category/note
  - status/finished
  - topic/tecnologie-web
date: 12-11-2024 20:37:13
links:
  - "[[Lecture 10102024151443]]"
---
# Header HTTP
---
## Introduzione
> Gli **header HTTP** compongono una [[Richiesta HTTP|richiesta]] e anche una [[Risposta HTTP|risposta]] [[HTTP]] e si dividono in:
> - _header generali_
> - _header di entità_
> - _header di richiesta/risposta_
> 
> Il loro compito è di specificare informazioni aggiuntive in merito allo scambio di messaggi HTTP.

### Header generali
Contengono informazioni sulla trasmissione. I principali sono:
- `Date`
- `Transfer-Encoding` - codifica usata per la trasmissioni
- `Cache-Control` - meccanismo di caching richiesto o suggerito per la risorsa
- `Connection` - tipo di connessione da usare

### Header di entità
Contengono informazioni sulla risorsa e sui dati trasmessi. I principali sono:
- `Content-Type` - il tipo [[MIME]] dell'entità del body
	- fondamentale, è solo grazie a questo che il client (per esempio) riesce a visualizzare l'oggetto ricevuto nel _body_
- `Content-Length`
- `Content-Encoding`, ecc...

### Header di richiesta/risposta
#### Richiesta
Posti dal client per specificare informazioni sulla richiesta e su se stesso al server:
- `User-Agent` - una stringa che descrive il client che origina la richiesta ([[Sistema operativo|sistema operativo]], [[Browser|browser]], ecc...)
- `Referer`
- `Host` - nome di dominio e porta a cui viene fatta la connessione

#### Risposta
Posti dal server per specificare informazioni sulla richiesta e su se stesso al client:
- `Server` - come `User-Agent` ma specchiato
- `WWW-Authenticate` - challenge usata per i meccanismi di autenticazione

## Referenze