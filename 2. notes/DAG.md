---
tags:
  - category/note
  - status/finished
  - topic/algoritmi-e-strutture-dati
date: 04-05-2024 19:44:41
links:
  - "[[Lecture 30042024111642]]"
---
# DAG
---
## Introduzione
> Un **DAG** (_Directed Acyclic Graph_) è un [[Grafo aciclico|grafo aciclico]] [[Grafo orientato|orientato]].

## Verifica
> Fissato un [[Grafo|grafo]] $G$ si ha che
> $$G \text{ è DAG} \iff \nexists \text{ archi all'indietro in visita DFS}$$
ovvero che se volessimo **verificare se un grafo è un [[DAG]] o meno ci basterebbe verificare che nella [[Foresta|foresta]] prodotta dalla [[DFS su grafi|visita DFS]] non esistano archi all'indietro**. Questo perché in un grafo orientato esiste un ciclo $\iff$ esiste un arco all'indietro nel grafo prodotto da una visita DFS.

Per implementare tale verifica direttamente sulla visita _ci basta controllare all'interno di `DFS-visit` se tra i vertici adiacenti del nodo analizzato ne esiste uno marcato `gray`_ (aperto): ecco spiegato il motivo per cui conviene usare 3 marcature e non 2 come avviene per la BFS.

## Referenze