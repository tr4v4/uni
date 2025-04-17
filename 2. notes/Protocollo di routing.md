---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 19-11-2024 19:21:16
links:
  - "[[Lecture 23102024132952]]"
  - "[[Lecture 15112024133341]]"
  - "[[Lecture 18032025163208]]"
---
# Protocollo di routing
---
## Introduzione
> Un **protocollo di routing** è un [[Algoritmo|algoritmo]] usato per instradare i pacchetti di [[Livello rete|livello rete]] dello [[Modello ISO-OSI|stack ISO-OSI]] _a seconda dell'indirizzo di destinazione e della condizione del traffico nella rete_.

## Idea
Tutti quanti gli algoritmi di routing, per cercare il cammino migliore per un pacchetto, si basano sull'idea di _inoltrare_ il pacchetto verso la strada che _in quel momento è quella ottimale_. Questo perché, trattandosi internet di un [[Servizio non orientato alla connessione|servizio non orientato alla connessione]], **non è possibile stabilire già in anticipo il percorso che il pacchetto dovrà percorrere**: _si esplora di [[Router|router]] in router_.

Di solito viene inviato un pacchetto "rompighiaccio" che permette a tutti i router attraversati di aggiornare le proprie tabelle (infatti ci metterà più tempo a rispondere); i successivi pacchetti saranno spediti secondo le regole di inoltro appena calcolate, _a patto di cambiamenti sostanziali nella topologia di rete_ (o nella congestione).

## Algoritmi
Gli algoritmi di routing si dividono in:
- _globali_ --> algoritmi che conoscono l'intera [[Topologia di rete|topologia della rete]];
- _distribuiti_ --> algoritmi che conoscono solo la topologia locale, limitati al loro parametro di orizzonte.

Inoltre, gli algoritmi si dividono in:
- _statici_ --> calcolati una sola volta e non più modificati (come [[Internet]]!);
- _dinamici_ --> calcolati più volte (come le reti mobili, ad esempio il wifi, in cui la topologia muta velocemente).

Sulla base della prima suddivisione, gli algoritmi sono detti:
- **link state** --> richiedono di conoscere l'intera rete, e sono algoritmi globali ([[Algoritmo di Djikstra]]);
- **distance vector** --> sono algoritmi decentralizzati, che si basano su messaggi di distanza ([[Algoritmo di Bellman-Ford]]).

Tra i due tipi di algoritmi, ci sono differenze in termini di:
- _complessita' dei messaggi_, LS richieste di inviare piu' messaggi rispetto a DV;
- _velocita' di convergenza_, LS potrebbe avere oscillazioni, ma DV richiede piu' tempo per convergere e potrebbe incorrere in loop infiniti;
- _robustezza_, in caso di errore LS potrebbe dare valori dei link errati, mentre DV potrebbe dare percorsi sbagliati (e propagare l'errore lungo la rete).

### Realta'
Nella realta' dei fatti, pero', Internet e' gerarchico, e i singoli router non possono conoscere tutta la sua topologia. Ci si affida agli [[Sistema autonomo|AS]] (Autonomous System), che sono delle **entita' logiche che raggruppano i router e i collegamenti tra di essi**.

All'_interno di ognuno di essi c'e' una regola di routing condivisa tra tutti i router_; tra _router di AS diversi bisogna fare un interfacciamento delle regole, attraverso i router di confine_.

In questo modo, si ha:
- **intra-AS routing** --> routing interno alle AS
	- [[RIP]]
	- [[OSPF]]
	- [[IGRP]]
- **inter-AS routing** --> routing tra AS
	- [[BGP]]

## Referenze