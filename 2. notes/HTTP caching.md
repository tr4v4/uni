---
tags:
  - category/note
  - status/finished
  - topic/tecnologie-web
  - topic/reti-di-calcolatori
date: 26-11-2024 20:02:04
links:
  - "[[Lecture 18122024132024]]"
  - "[[Lecture 20122024133953]]"
---
# HTTP caching
---
## Introduzione
> La **caching HTTP** è un meccanismo offerto da [[HTTP]] che permette di _memorizzare temporaneamente le risorse_ richieste dai client, al fine di _migliorare le prestazioni_.

E' molto utile soprattutto in applicazioni [[REST|RESTful]].

## Tipologie
Può essere:
- **server-side**: il server memorizza le risorse, riducendo i tempi di computazione ma non riducendo il carico sulla rete;
- **client-side**: il client memorizza le risorse.
- **proxy-side**: un [[Proxy|proxy]] memorizza le risorse.

## Cache control
Per controllare la validità dei dati in cache, HTTP-1 introduce 2 meccanismi di controllo:
- _server-specified expiration_;
- _heuristic expiration_.

### Server-specified expiration
Il **server indica una scadenza della risorsa**, usando l'[[Header HTTP|header]] `Expires` o `Cache-Control`.

Con `Expires`, se la data di scadenza è già passata, la richiesta deve essere rivalidata. Tuttavia, in caso la richiesta accetti risposte scadute o l'_origin server_ non può essere raggiunto, la cache può rispondere con la risposta scaduta ma con il [[Status code|codice di ritorno]] `110` (_Response is stale_).

L'header `Cache-Control` permette di controllare altri comportamenti della cache, specificando delle direttive:
- _must-revalidate_: la risposta scaduta non può mai essere rispedita --> la risorsa dev'essere presa dall'origin server, e in caso di mancata risposta la cache deve rispondere con `504` (_Gateway timeout_);
- _no-cache_: la richiesta deve sempre essere rivalidata;

### Heuristic expiration
In mancanza di un'indicazione di scadenza da parte del server, **la cache può calcolare autonomamente la scadenza stabilendo valori euristici di durata delle risorse**. Usa informazioni contenute in altri header (come `Last-Modified`) per calcolare la scadenza. L'algoritmo non è fissato nelle specifiche HTTP, ma è lasciato all'implementazione della cache.

Questo meccanismo è meno preciso, ma permette di ridurre il carico sui server. Infatti, in caso di "indecisione", la cache deve fornire un codice `113` (_Heuristic expiration_) alla risposta.

## Validazione
Nella maggior parte dei casi, anche dopo la scadenza della risorsa, questa _non sarà stata modificata_, e quindi _tecnicamente la cache potrebbe continuare a servirla_.
Ci sono 2 modi per verificarlo:
- _usare `HEAD`_: la cache fa la richiesta, e verifica l'ultima data di modifica (richiede una richiesta in più);
- _usare una richiesta condizionale con appositi header_ (`If-Modified-Since` e `If-None-Match`): se la risorsa è stata modificata, il server risponderà con un `200 OK` e la risorsa aggiornata, altrimenti con un `304 Not Modified` e il body vuoto, riducendo il numero di richieste.

## Referenze