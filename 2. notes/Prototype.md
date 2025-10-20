---
tags:
  - category/note
  - status/finished
  - topic/ingegneria-del-software
date: 20-10-2025 16:39:17
links:
---
# Prototype
---
## Introduzione
> Il **prototype** è un [[Design patterns creazionali|design pattern creazionale]] usato in alternativa al [[Factory method|factory method]] per cercare di ridurre il numero di sottoclassi parallele.

E' basato proprio sul concetto di [[Prototipo|prototipo]], e in particolare su quello di _clonazione_. Si usa semplicemente per evitare di fare delle `new`: queste possono essere costose. Allora, _si parte da un prototipo già costruito, di default, e se ne fa una copia esatta ogni qualvolta che un client ne dovesse avere bisogno_.

Con la factory, quindi, si crea un nuovo oggetto; con il prototipo, se ne clona uno già esistente.

## UML
Si rappresenta attraverso il seguente [[Diagramma delle classi|diagramma delle classi]] [[UML]]:
![[prototype-uml.png]]

## Referenze