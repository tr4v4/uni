---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 14-12-2024 17:46:42
links:
  - "[[Lecture 29112024132404]]"
---
# Congestione di rete
---
## Introduzione
> La **congestione di rete** è un fenomeno che si verifica quando il _carico di traffico su una [[Rete|rete]] supera la sua capacità massima_.

## Cause
Il [[Router|router]] quando riceve un [[Pacchetto|pacchetto]] ma ne sta già elaborando un altro, lo inserisce in un _buffer_ ([[Coda|coda]]). Quando il buffer di ricezione si riempie del tutto, **il router non ha più spazio per memorizzare i pacchetti in arrivo e deve scartarli**: questa si chiama **congestione** della rete.

Si deve quindi evitare che i router siano sovraccaricati di pacchetti, _diminuendo in qualche maniera il ritmo di trasmissione dei pacchetti_.

## Soluzioni
La soluzione _naive_ al problema consiste nell'[[ECN]] (_Explicit Congestion Notification_), una tecnica che consisteva nell'_invio di un pacchetto che il router congestionato inviava agli altri router a catena fino al mittente per avvisarlo della congestione in atto_. Questo, una volta ricevuto il pacchetto, avrebbe diminuito il ritmo di trasmissione dei pacchetti.

Il problema di questo approccio è che potrebbe amplificare la congestione, nel tentativo di risolverla! Infatti **i pacchetti di notifica della congestione potrebbero essere scartati a loro volta, generando un effetto domino** che non farebbe altro che diffondere la congestione su tutta la rete.

In poche parole, i router non hanno sufficienti capacità[^1] per poter risolvere il problema in modo autonomo: **bisogna agire sui mittenti**. Se infatti _tutti i mittenti si mettono d'accordo a inviare pacchetti più lentamente, la congestione si risolve da sola_.

Questo è ciò che avviene nel meccanismo di [[Controllo della congestione|controllo della congestione]] implementato dal [[TCP]].

## Referenze
[^1]: una sorta di [[Potere espressivo|potere espressivo]]