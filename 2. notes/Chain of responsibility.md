---
tags:
  - category/note
  - status/finished
  - topic/ingegneria-del-software
date: 20-10-2025 18:43:57
links:
---
# Chain of responsibility
---
## Introduzione
> Il **chain of responsibility** è un [[Design patterns comportamentali|design pattern comportamentale]] usato quando _si ha una richiesta da soddisfare, ma non si sa in anticipo chi sia in grado di gestirla_.

Di base si concatena l'oggetto ricevuto e si passa al prossimo "nodo" fino a che un oggetto non è in grado di gestirlo.

Consente di **diminuire il coupling tra il sender e il receiver**, in relazione al [[Design di sistemi software#Low coupling|low coupling]].

## UML
Si rappresenta attraverso il seguente [[Diagramma delle classi|diagramma delle classi]] [[UML]]:
![[chain-of-responsibility-uml.png]]

Si implementa quindi tramite una **[[Lista#Liste concatenate|lista concatenata]] di gestori di richieste**.

## Referenze