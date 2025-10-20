---
tags:
  - category/note
  - status/finished
  - topic/ingegneria-del-software
date: 20-10-2025 16:32:27
links:
---
# Factory method
---
## Introduzione
> Il **factory method** è un [[Design patterns creazionali|design pattern creazionale]] per la _creazione di un oggetto cui informazione necessaria per la sua costruzione è disponibile solo a run-time_.

Fondamentalmente se una classe non può anticipare la classe dell'oggetto che deve creare, possiamo creare un'[[Interfaccia|interfaccia]] e lasciar decidere alle sottoclassi che classe istanziare.

Di base, il factory method sfrutta tanto il [[Polimorfismo|polimorfismo]], basandosi fortemente sull'[[Ereditarietà|ereditarietà]].

## UML
Si rappresenta attraverso il seguente [[Diagramma delle classi|diagramma delle classi]] [[UML]]:
![[factory-method-uml.png]]

## Referenze