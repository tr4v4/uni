---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 19-11-2024 19:21:16
links:
  - "[[Lecture 23102024132952]]"
  - "[[Lecture 15112024133341]]"
---
# Protocollo di routing
---
## Introduzione
> Un **protocollo di routing** è un [[Algoritmo|algoritmo]] usato per instradare i pacchetti di [[Livello rete|livello rete]] dello [[Modello ISO-OSI|stack ISO-OSI]] _a seconda dell'indirizzo di destinazione e della condizione del traffico nella rete_.

## Idea
Tutti quanti gli algoritmi di routing, per cercare il cammino migliore per un pacchetto, si basano sull'idea di _inoltrare_ il pacchetto verso la strada che _in quel momento è quella ottimale_. Questo perché, trattandosi internet di un [[Servizio non orientato alla connessione|servizio non orientato alla connessione]], **non è possibile stabilire già in anticipo il percorso che il pacchetto dovrà percorrere**: _si esplora di [[Router|router]] in router_.

Di solito viene inviato un pacchetto "rompighiaccio" che permette a tutti i router attraversati di aggiornare le proprie tabelle (infatti ci metterà più tempo a rispondere); i successivi pacchetti saranno spediti secondo le regole di inoltro appena calcolate, _a patto di cambiamenti sostanziali nella topologia di rete_ (o nella congestione).

## Protocolli
I protocolli più importanti sono:
- [[RIP]] - Routing Information Protocol
- [[OSPF]] - Open Shortest Path First
- [[BGP]] - Border Gateway Protocol (usato tra router di [[Sistema autonomo|AS]])

## Referenze