---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 13-07-2025 16:30:28
links:
  - "[[Lecture 29042025152102]]"
---
# Ethernet
---
## Introduzione
> Il **protocollo Ethernet** è un [[Protocollo di rete|protocollo di rete]] del [[Livello MAC-LLC|livello MAC-LLC]] che si occupa della _gestione dell'accesso al mezzo trasmissivo in una rete cablata_. È definito dallo standard IEEE 802.3.

## Funzionamento
Fondamentalmente, quando un dispositivo vuole trasmettere dei dati segue i seguenti passi:
1. _ascolta il canale per verificare se e' libero_;
2. _se il canale è libero, inizia a trasmettere i dati_;
3. _mentre trasmetto i dati ascolto il canale per verificare se ci sono collisioni_;
4. _se c'e' una collisione_, _attendo un tempo casuale prima di riprovare a trasmettere_;
5. _ogni volta che si verifica una collisione, raddoppio il tempo di attesa prima di riprovare a trasmettere_.

Si tratta di un protocollo **best-effort**: non viene garantito che prima poi i dati vengano trasmessi.

<u>Nota bene</u>: con [[Token Ring]] questo problema non si pone, perché il token permette di evitare le collisioni.

Ora, _le collisioni di solito sono rare_, perche' la _[[Topologia di rete|topologia]] standard di Ethernet e' a stella_ e si usa uno _[[Switch|switch]] che regola il tutto_. Se pero' ci fosse un [[Hub|hub]] (che fa broadcast), questa sicurezza non ci sarebbe e Ethernet dovrebbe gestire piu' collisioni.

## Referenze