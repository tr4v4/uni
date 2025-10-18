---
tags:
  - category/note
  - status/finished
  - topic/ingegneria-del-software
date: 14-10-2025 12:04:36
links:
  - "[[Lecture 13102025104920]]"
---
# Diagramma dei componenti
---
## Introduzione
> I **diagrammi dei componenti** sono diagrammi [[UML]] per la scrittura in [[OOD|fase di design]] dei [[Componente|componenti]].

### Componente
Un componente e' rappresentato da un quadrato con 2 barre, come una sorta di circuito integrato. All'esterno e' possibile indicare con dei cerchi le interfacce che implementa, ed esplicitare altri componenti che realizzano la collaborazione con il componente che le implementa:
![[componente-uml.png]]

## Relazioni
Le relazioni sono 2:
- realizzazione
- dipendenza

esattamente come quelle dei [[Diagramma delle classi|diagrammi delle classi]].

## Stereotipi
Posso assegnare dei tag ad ogni componente, per specificare il loro tipo:
- executable
- library
- table
- file
- document

![[componenti-stereotipi.png]]

## Referenze