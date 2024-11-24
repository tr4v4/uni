---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 19-11-2024 18:20:09
links:
  - "[[Lecture 09102024132027]]"
  - "[[Lecture 23102024132952]]"
---
# Livello fisico
---
## Introduzione
> Il **livello fisico** è il primo dei 7 livello del [[Modello ISO-OSI|modello ISO-OSI]] che si occupa della **codifica e decodifica dei dati**. In questo livello, _i dati digitali sono rappresentati come bit_ e la loro avviene tramite _segnali analogici_.

L'idea è che si vuole **codificare dei dati digitali** (_bit_) **in segnali analogici**, per poterli trasmettere su un mezzo fisico.

## Definizioni
Prima di analizzare il livello fisico, è necessario definire alcuni termini chiave:
- _velocità di trasmissione_: a seconda del mezzo trasmissivo, è la velocità a cui viaggia il segnale analogico (cavo in rame è la velocità della corrente, fibra ottica e onde elettromagnetiche è la velocità della luce, ecc.);
- _capacità del canale di trasmissione_: è il valore massimo di bit/secondo che può trasmettere il canale;
- _throughput_: è il valore massimo di bit utili/secondo, ossia di bit di dati effettivi (non quelli usati dai [[Protocollo di rete|protocolli di rete]]).

Se la prima è determinata dalle leggi fisiche naturali, la seconda invece **dipende strettamente dal tempo necessario alla codifica e decodifica del valore di ogni bit**. Infatti, ciò che determina la capacità di trasmissione è, metaforicamente, la dimensione del "cassetto" assegnato a ogni bit, indice del tempo di trasmissione di un bit.

Quindi: una _capacità alta significa una durata di rappresentazione dei simboli_ (contenitori di bit) _ridotta_. Tuttavia, non sempre la capacità è alta, infatti:
- l'_abilità del ricevente di leggere e salvare ogni simbolo_ può richiedere una capacità più bassa per avere più tempo;
- _eventuali disturbi nella trasmissione che offuscano la visione dei simboli_, per cui conviene al ricevente avere più tempo per leggerli.

In poche parole: **la capacità è un vincolo non della trasmissione ma della ricezione**!

## Dispositivi
I dispositivi che operano a livello fisico sono:
- [[Repeater|repeater]]: dispositivo che _ripete il segnale ricevuto amplificandolo_;
- [[Hub|hub]]: dispositivo che _ripete il segnale ricevuto e lo invia a tutti i dispositivi connessi_ (in broadcast);

## Referenze