---
tags:
  - category/note
  - status/finished
  - topic/ingegneria-del-software
date: 20-10-2025 16:07:26
links:
---
# Abstract factory
---
## Introduzione
> L'**abstract factory** è un [[Design patterns creazionali|design pattern creazionale]] per la creazione di famiglie di oggetti dipendenti senza specificare le loro classi concrete. E' utile per avere una molteplicità di famiglie di prodotti di cui si vuole nascondere l'implementazione, mostrando solo l'interfaccia.

## UML
Si rappresenta attraverso il seguente [[Diagramma delle classi|diagramma delle classi]] [[UML]]:
![[abstract-factory-uml.png]]

## Utilizzo
```Java
AbstractFactory f;
AbstractComponent1 c1;
AbstractComponent2 c2;

// We want component 1 from Family A.
f = new FamilyAFactory();
c1 = f.createComponent1();

// We want component 2 from Family C.
f = new FamilyCFactory();
c2 = f.createComponent2();
```

## Referenze