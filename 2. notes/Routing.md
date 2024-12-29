---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 19-11-2024 21:13:33
links:
  - "[[Lecture 14112024173206]]"
  - "[[Lecture 15112024133341]]"
---
# Routing
---
## Introduzione
> Il **routing** è il processo di _trasmissione dei pacchetti da un host sorgente a un host destinatario attraverso una serie di nodi intermedi_. Viene effettuato dai [[Router|router]].

## Funzionamento
### Gerarchia ad albero
Se la gerarchia della rete è ad albero, l'instradamento è banale: il pacchetto viene inviato al _default gateway_ se il destinatario non fa parte della rete; altrimenti viene inoltrato al segmento corretto.

### Gerarchia non ad albero
Se la gerarchia della rete non è ad albero, ossia quando siamo al livello della radice dell'albero, il router non ha padri ma solo fratelli. In questo caso il router deve necessariamente ricorrere a una **tabella di instradamento**, costantemente aggiornata dagli [[Protocollo di routing|algoritmi di routing]].

Il router di destinazione usa a sua volta una tabella di instradamento sulle sue sottoreti, che consente di inoltrare al router della sottorete di destinazione corretta - il router di destinazione, a sua volta, inoltra il pacchetto al destinatario finale.

<u>Nota bene</u>: ogni router ha una linea dedicata per ognuno dei fratelli, ossia una scheda di rete.

## Aggiornamento
L'aggiornamento delle tabelle di forwarding dei router è un processo continuo, che può essere influenzato da un numero illimitato di ragioni, tra cui le modifiche degli accordi di servizio tra i gestori di [[Sistema autonomo|sistemi autonomi]] (AS).

Quando si verifica, per esempio, un guasto di un [[Mezzo di trasmissione|mezzo trasmissivo]], le tabelle di routing dei router circostanti rimangono invariate fino a che non viene "captata" la rottura di un arco: _finché ciò non avviene tali tabelle contengono indicazioni errate sull'instradamento dei pacchetti, con conseguente eventuale perdita di alcuni di essi_. Questo è la causa del [[Servizio non orientato alla connessione|servizio non orientato alla connessione]] del livello rete, per cui si dice essere _best-effort_!

## Referenze