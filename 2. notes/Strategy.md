---
tags:
  - category/note
  - status/finished
  - topic/ingegneria-del-software
date: 20-10-2025 18:36:24
links:
---
# Strategy
---
## Introduzione
> Lo **strategy** è un [[Design patterns comportamentali|design pattern comportamentale]] cui obiettivo è quello di _parametrizzare oggetti con molteplici comportamenti a run-time_.

Elimina la necessità di porre delle condizioni definendo una famiglia di [[Algoritmo|algoritmi]], e incapsulando ognuno di essi in modo che siano interscambiabili.

## UML
Si rappresenta attraverso il seguente [[Diagramma delle classi|diagramma delle classi]] [[UML]]:
![[strategy-uml.png]]

In questo caso, quindi, l'entità in gioco contiene una strategia, che può cambiarsi anche a run-time con una delle implementazioni possibili di `Strategy`. Se non esistesse questo pattern, **`Entity` conterrebbe `action()` e al suo interno ci dovrebbe essere uno `switch` per decidere quale algoritmo usare in base a una condizione**.

## Referenze