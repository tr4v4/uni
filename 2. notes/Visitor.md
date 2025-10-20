---
tags:
  - category/note
  - status/finished
  - topic/ingegneria-del-software
date: 20-10-2025 18:27:29
links:
---
# Visitor
---
## Introduzione
> Il **visitor** è un [[Design patterns comportamentali|design pattern comportamentale]] implementato come una _[[Classe|classe]] che definisce un'operazione da eseguire sugli elementi di una struttura di un oggetto_.

E' l'**oggetto visitato che decide in che modo avviene la visita**.

## UML
Si rappresenta attraverso il seguente [[Diagramma delle classi|diagramma delle classi]] [[UML]]:
![[visitor-uml.png]]

Ogni elemento, di qualunque tipo, ha un metodo `accept` che accetta un `Visitor` generico (ce ne possono essere di tanti tipi). Questo metodo **chiama un metodo, a scelta sua, di visita dei `Visitor` su se stesso**.

## Referenze