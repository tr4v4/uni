---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 08-10-2024 19:41:11
links:
  - "[[Lecture 27092024132110]]"
---
# Commutazione di circuito
---
## Introduzione
> Le [[Rete|reti]] a **commutazione di circuito** _riservano un circuito di [[Canale di comunicazione|canali di comunicazione]] punto a punto su ogni connessione lungo tutto il cammino dal mittente al destinatario_.

Nel dettaglio, viene stabilito un canale riservato tra due dispositivi su più reti diverse, indifferentemente dai [[Mezzo di trasmissione|mezzi trasmissivi]].

La rete telefonica è a commutazione di circuito.

## Funzionamento
Per stabilire il canale punto a punto (o anche ad accesso multiplo) a partire dal mittente, ogni _hop_ deve _chiedere di riservare un canale fino ad arrivare al destinatario_. Una volta arrivata la richiesta al destinatario, se questo accetta, il canale viene confermato e viene stabilita la connessione tra i due interlocutori: **è come se questi fossero virtualmente in comunicazione diretta (punto a punto) tra di loro**.
![[commutazione-di-circuito.png]]

### Vantaggi
Stabilito il canale, il _ritardo di comunicazione è molto basso_. Inoltre _si risparmia per ogni messaggio l'overhead degli indirizzamenti_: sia che il canale sia punto a punto o che sia ad accesso multiplo, _una volta che è stata stabilita la connessione tutti gli interlocutori appartenenti al "circuito virtuale" ricevono il messaggio_, per cui non c'è bisogno di specificare gli indirizzi.

### Svantaggi
Tutto questo si paga ovviamente in _tempo di connessione_: per stabilire il circuito virtuale, infatti, _bisogna aspettare che ogni hop riservi il canale_. Inoltre il canale viene sprecato in momenti di "silenzio".

## Referenze