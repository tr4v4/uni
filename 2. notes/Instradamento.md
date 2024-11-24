---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 19-11-2024 21:13:33
links:
  - "[[Lecture 14112024173206]]"
---
# Instradamento
---
## Introduzione
> L'**instradamento** è il processo di _trasmissione dei pacchetti da un host sorgente a un host destinatario attraverso una serie di nodi intermedi_. Viene effettuato dai [[Router|router]].

## Funzionamento
### Gerarchia ad albero
Se la gerarchia della rete è ad albero, l'instradamento è banale: il pacchetto viene inviato al _default gateway_ se il destinatario non fa parte della rete; altrimenti viene inoltrato al segmento corretto.

### Gerarchia non ad albero
Se la gerarchia della rete non è ad albero, ossia quando siamo al livello della radice dell'albero, il router non ha padri ma solo fratelli. In questo caso il router deve necessariamente ricorrere a una **tabella di instradamento**, costantemente aggiornata dagli [[Protocollo di routing|algoritmi di routing]].

<u>Nota bene</u>: ogni router ha una linea dedicata per ognuno dei fratelli, ossia una scheda di rete.

Il router di destinazione usa a sua volta una tabella di instradamento sulle sue sottoreti, che consente di inoltrare al router della sottorete di destinazione corretta - il router di destinazione, a sua volta, inoltra il pacchetto al destinatario finale.

## Referenze