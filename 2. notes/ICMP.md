---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 13-12-2024 16:53:07
links:
  - "[[Lecture 15112024133341]]"
---
# ICMP
---
## Introduzione
> L'**ICMP** (_Internet Control Message Protocol_) è un [[Protocollo di rete|protocollo]] del [[Livello rete|livello rete]] usato dagli host, [[Router|router]] e gateway per scambiare informazioni riguardanti
> - i cammini percorsi da un pacchetto,
> - gli errori di configurazione di router,
> - le [[Prestazione delle reti|prestazioni della rete]]
> - e tanto altro,
>  
> usando pacchetti definiti con il protocollo [[IP]].

## Informazioni
Le informazioni contenute in messaggi ICMP possono essere:
- _rete di destinazione non raggiungibile_;
- _rete di destinazione sconosciuta_;
- _host di destinazione non raggiungibile_;
- _host di destinazione sconosciuto_;
- _protocollo richiesto non disponibile_;
- _ricerca di un cammino alternativo per la destinazione_;
- ecc...

## Applicazioni
I messaggi ICMP sono usati da diverse applicazioni a seconda del loro scopo. In particolare se ne citano le due più famose:
- [[Ping|ping]]
- [[Traceroute|traceroute]]

## Referenze