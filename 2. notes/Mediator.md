---
tags:
  - category/note
  - status/finished
  - topic/ingegneria-del-software
date: 20-10-2025 19:01:39
links:
---
# Mediator
---
## Introduzione
> Il **mediator** è un [[Design patterns comportamentali|design pattern comportamentale]] usato _quando tra oggetti diversi ci sono interazioni complesse e non vogliamo che queste siano incluse negli oggetti stessi_.

Fondamentalmente è uno "spazio" usato dagli oggetti per condividere le informazioni e centralizzare il controllo. Chiaramente, il **mediatore deve avere un [[Insieme|insieme]] fisso di primitive che devono essere conosciute da ogni partecipante**[^1].

## UML
Si rappresenta attraverso il seguente [[Diagramma delle classi|diagramma delle classi]] [[UML]]:
![[mediator-uml.png]]

## Referenze

[^1]: stesso principio del [[Protocollo|protocollo]]
