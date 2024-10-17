---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 08-10-2024 19:50:04
links:
  - "[[Lecture 27092024132110]]"
---
# Commutazione di pacchetto
---
## Introduzione
> Le [[Rete|reti]] a **commutazione di pacchetto** _suddividono i dati inviati in pacchetti indipendenti che viaggiano separatamente su un unico [[Canale di comunicazione|canale]] ad accesso multiplo_.

La rete internet è basata sulla commutazione di pacchetto.

## Funzionamento
Su canali ad accesso multiplo, in particolare, _ogni pacchetto deve contenere l'indirizzo del destinatario e del mittente_. Questi viaggiano su uno stesso canale condiviso dal mittente al destinatario. I nodi intermedi, gli _hop_, devono attuare un meccanismo di ricezione e inoltro dei pacchetti.

Su _canali punto a punto invece la commutazione di pacchetto ha poco senso_: i dati sono discretizzati, e quindi tra l'invio di un pacchetto e un altro passa del tempo che non è sfruttato.

![[commutazione-di-pacchetto.png]]

### Vantaggi
Rispetto alla [[Commutazione di circuito|commutazione di circuito]], vengono utilizzate _meno risorse di rete_ (canali e connessioni) _ma in modo più efficiente_. Inoltre non stabilendo un canale per tot. tempo, _la connessione si "paga" per quantità di pacchetti inviati (dati trasmessi) e non per il tempo di utilizzo del canale_.

### Svantaggi
Ovviamente, il meccanismo di ricezione e inoltro dei pacchetti attuato dagli _hop_ occupa un tempo che sommato causa un _maggiore ritardo della rete_.

## Conseguenze
Questo paradigma di connessione ha quindi le seguenti principali proprietà:
- _i dati sono spediti in pacchetti con indicato mittente e destinatario_;
- _ad ogni nodo intermedio i pacchetti sono immagazzinati e inoltrati verso il destinatario finale_.

Questo comporta la possibilità di **perdita dei pacchetti** e di **arrivo disordinato di pacchetti**. La gestione di queste possibilità è chiamata _servizio di trasmissione_, e ce ne sono di due tipi:
- [[Servizio orientato alla connessione|orientati alla connessione]];
- [[Servizio non orientato alla connessione|non orientato alla connessione]].

## Referenze