---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 08-10-2024 20:06:05
links:
  - "[[Lecture 27092024132110]]"
---
# Servizio orientato alla connessione
---
## Introduzione
> I **servizi orientati alla connessione** nelle [[Rete|reti]] a [[Commutazione di pacchetto|commutazione di pacchetto]] garantiscono:
> 1. _la consegna ordinata dei pacchetti ricevuti, secondo l'ordine di invio_;
> 2. _la ritrasmissione di eventuali pacchetti perduti_.

Sono attuati da protocolli che possono agire in vari modi:
- creazione di un "circuito virtuale", con astrazione della connessione logica in canale punto a punto tale per cui _i pacchetti devono seguire un unico percorso e mantenersi in fila_;
- numerazione dei pacchetti, con _riordine da parte del destinatario una volta ricevuti_ e _richiesta di rinvio per quelli persi_.

## Referenze