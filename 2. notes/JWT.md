---
tags:
  - category/note
  - status/finished
  - topic/tecnologie-web
date: 26-11-2024 19:33:40
links:
---
# JWT
---
## Introduzione
> Il **JWT (JSON Web Token)** è uno standard che definisce un _formato [[JSON]] per lo scambio di [[Autenticazione token-based|token di autenticazione]]_, e più in generale di informazioni (detti _claims_) tra servizi [[Web|web]].

Il meccanismo è generico e permette così di:
- personalizzare i claim;
- usare [[Algoritmo|algoritmi]] diversi per firmare i messaggi.

## Struttura
Un token JWT è composto da tre parti separate da un punto `.` e ottenute codificando i dati in input in [[Base64|base64]]:
1. **header**: contiene il tipo del token e l'algoritmo di cifratura utilizzato;
2. **payload**: contiene i claims, ovvero le informazioni di interscambio che si vogliono trasmettere, organizzate in
	- _registered claims_: claims predefiniti, come `iat` (issued at) `iss` (issuer), `exp` (expiration time), `sub` (subject), `aud` (audience);
	- _public claims_: claims definiti da chiunque ma dichiarati nello [[IANA]] JSON Web Token Claims Registry per evitare conflitti;
	- _private claims_: claims definiti dalle parti che scambiano il token;
3. **signature**: contiene la firma del token, che permette di verificare l'integrità dei dati.

<u>Nota bene</u>: _il contenuto del token non è cifrato, ma solo codificato in base64_! Si può decodificare facilmente, non bisogna inserire dati sensibili.

## Referenze