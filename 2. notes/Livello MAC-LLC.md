---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 19-11-2024 18:23:55
links:
  - "[[Lecture 09102024132027]]"
  - "[[Lecture 23102024132952]]"
  - "[[Lecture 20112024140334]]"
---
# Livello MAC-LLC
---
## Introduzione
> Il **livello MAC-LLC** (_Media Access Control-Logical Link Control_) è il secondo dei 7 livelli del [[Modello ISO-OSI|modello ISO-OSI]] e si occupa della **gestione dell'accesso al mezzo trasmissivo** e del **controllo logico della connessione**. In particolare fornisce delle _regole di indirizzamento dei dispositivi all'interno della [[LAN|rete locale]]_ e di gestione della comunicazione tra di essi.

## Compiti
Il livello MAC-LLC si occupa di:
- _accesso al mezzo trasmissivo_ -> gestisce l'accesso al mezzo trasmissivo, in particolare _risolve le collisioni_ in una rete condivisa;
- _indirizzamento_ -> assegna un [[Indirizzo MAC|indirizzo MAC]], un indirizzo fisico, univoco a ogni dispositivo connesso alla rete;
- _controllo dell'errore_ -> _rileva e corregge gli errori_ di trasmissione;

## Dispositivi
I dispositivi che operano a questo livello sono:
- [[Bridge|bridge]]: dispositivo che _interconnette due o più segmenti di rete locale_, con tecnologie MAC diverse (esempio uno [[Ethernet]] con uno [[Token Ring]], lo stesso [[Access point]] è un bridge tra 802.3 e 802.11, [[Wi-Fi]]);
- [[Switch|switch]]: dispositivo analogo al bridge, ma permette di connettere molti segmenti (fino a 10-12), e in più _indirizza i pacchetti sul segmento giusto in base all'indirizzo MAC del destinatario_.

## Protocolli
I protocolli che operano a questo livello sono:
- [[ARP]] e [[RARP]];
- [[MAC]];

## Referenze