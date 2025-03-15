---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 23-02-2025 19:20:08
links:
  - "[[Lecture 29112024132404]]"
---
# Sliding window
---
## Introduzione
> Per **sliding window** (o **finestra scorrevole**) si intende un meccanismo di [[Controllo della congestione|controllo della congestione]] e di [[Controllo del flusso|controllo del flusso]] adottato dal [[TCP]].

Un'idea naive per fare il controllo della congestione potrebbe essere quello di inviare un pacchetto sonda che ci dice _quanto la rete e' congestionata sulla base del tempo di invio e di ricezione_, quindi sulla base del risultato inviare piu' o meno pacchetti.
Questa tecnica, pero', _causa delle oscillazioni nelle congestioni_: se tutti ragionano cosi' si inviano pacchetti a raffica da ogni sorgente e si congestionano i [[Router|router]], che poi si liberano e si congestionano di nuovo, in un loop sinusoidale.

## Idea
L'idea della finestra scorrevole e' intelligente. Si tratta di fatto di un **numero intero che rappresenta il numero massimo di segmenti che puo' inviare il mittente senza ricevere conferma**. La finestra e' "sliding" perche' si sposta in base alle conferme ricevute.

Inoltre la dimensione della finestra e' variabile, e si adatta allo stato di congestione della rete.

Risolve quindi il problema del controllo della congestione, ma anche il controllo del flusso: _la grandezza della sliding window viene negoziata nel [[Three-way handshake|three-way handshake]] sulla base delle capacita' di ricezione del destinatario_!
Infatti, la **finestra scorrevole viene calcolata come la minima tra la finestra di congestione** (calcolata di seguito) **e la finestra di flusso** (negoziata con il destinatario).

### Funzionamento
Fondamentalmente la **finestra parte da 1**, e ad ogni ricezione avvenuta correttamente **raddoppia**, fino ad arrivare a un limite massimo (definito nel three-way handshake). Ogni volta che si verifica una **congestione, segnalata dalla mancata ricezione di un ACK (scatta il timeout), la finestra torna ad 1**!

Quest'operazione "drastica" _la si fa su reti [[Ethernet]]_, dove la congestione e' la causa piu' probabile della perdita di un pacchetti. Su _reti wireless_ la perdita di un pacchetto e' causata piu' probabilmente da interferenze, per cui _la finestra viene dimezzata_.

### Conseguenze
Se facciamo un grafico della sliding window rispetto al tempo, vediamo che la finestra cresce esponenzialmente fino a un certo punto, e poi decresce istantaneamente (torna a 1), e così via: questo andamento è detto a _sawtooth_ (dente di sega). Il _numero di pacchetti sulla rete in media si calcola come la [[Teorema della media integrale|media integrale]] della sawtooth_!

## Referenze