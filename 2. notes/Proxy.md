---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 02-03-2025 19:20:06
links:
  - "[[Lecture 18122024132024]]"
---
# Proxy
---
## Introduzione
> Il **proxy** e' un [[Server|server]] di prossimita', usato solitamente _per implementare il meccanismo di [[HTTP caching]] in modo da memorizzare le informazioni restituite dal server ai client e migliorare quindi l'efficienza delle [[Rete|reti]]_.

## Funzionamento
Gli step sono i seguenti:
1. il client fa <u>sempre</u> la richiesta al proxy;
2. se il proxy ha la risposta in [[Cache|cache]] (**cache-hit**!) allora la restituisce al client;
3. se il proxy non ha la risposta in cache (**cache-miss**!) allora inoltra la richiesta al server (`Origin-server`);
4. quando il server risponde al proxy, questo memorizza in cache la [[Risorsa|risorsa]] [[Web|web]], cosi' da soddisfare future richieste della stessa;

## Impatto
L'HTTP caching implementato con il proxy ha notevoli vantaggi, sia per i client che per i server: **abbassa la velocita' dei tempi di risposta dell'intero web**.

Preso anche solo il caso di una rete [[LAN]] di $n$ dispositivi che vogliono accedere a risorse web su [[Internet|internet]], se tra i [[Router|router]] tra le due reti si forma un collo di bottiglia, si rischia di mandare in [[Congestione di rete|congestione]] la rete, provocando ritardi nelle risposte.
Una soluzione potrebbe essere di aumentare la [[Prestazione delle reti#Capacità di trasmissione|capacita' di trasmissione]] tra le due reti, ma e' estremamente costoso. Con un _proxy locale, con un cache-hit rate sufficientemente alto, si risolve il problema spendendo pochissimo_.

## Caratteristiche
Il proxy non e' usato con il solo scopo di implementare caching HTTP. Di fatto fornisce "involontariamente" servizi al server e al client:
- **anonimizza le richieste**, infatti il server riceve solo dal proxy, per cui i _log_ risultano inutili;
	- a scopi di ricerca legale e' infatti richiesta l'apertura dei log dei proxy, che spesso e volentieri, pero', non lo permettono!
- **limita le richieste**, filtrando alcune richieste al server, sulla base di certe politiche;
- **pone un problema alla privacy**, nel caso in cui il proxy fungesse da _man-in-the-middle_;

## Referenze