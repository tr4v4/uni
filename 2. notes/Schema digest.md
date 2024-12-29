---
tags:
  - category/note
  - status/finished
  - topic/tecnologie-web
date: 26-11-2024 18:35:39
links:
---
# Schema digest
---
## Introduzione
> Lo **schema digest** è uno degli [[WWW-Authenticate|schemi di autenticazione]] [[HTTP]] più comuni. Si tratta di un metodo _più sicuro del [[Schema basic|basic]]_, che _richiede al client di inviare un [[Hash|hash]] delle credenziali_.

## Funzionamento
Il client, in risposta al codice di stato `401` (_Unauthorized_) e all'header `WWW-Authenticate` specifico, invia una _fingerprint_ della password, ossia la password passata a una [[Funzione hash|funzione hash]] (come [[MD5]]).

Per evitare _[[Attacco replay|attacchi di tipo replay]]_, il server invia al client un _nonce_, un numero casuale che il client deve includere nel calcolo dell'hash.
![[schema-digest.png]]

## Referenze