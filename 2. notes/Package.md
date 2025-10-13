---
tags:
  - category/note
  - status/finished
  - topic/ingegneria-del-software
date: 06-10-2025 19:23:07
links:
  - "[[Lecture 06102025160756]]"
---
# Package
---
## Introduzione
> Un **package** e' un'_unita' di deploy_.

Contiene anche una lista di dipendenze dagli altri package, indicati esplicitamente con `import`. L'obiettivo e' di _minimizzare tali dipendenze_, senza pero' fare un mega-package che contenga tutto il codice!

### Ridurre complessita' dell'interfaccia
Potremmo voler ridurre la complessita' dell'interfaccia di un package, attraverso:
- una classe pubblica che espone il comportamento del package;
- delegare le operazioni pubbliche a una classe appropriata all'interno del package;
- ...

Ma non sono soluzioni ottime...

### Pacchetti vs. diagrammi
I pacchetti rappresentano la divisione fisica dello sviluppo da fare. Servono per semplificare la definizione dei workpackages e per sviluppare sistemi software.

I [[UML|diagrammi]], invece, rappresentano l'assemblamento logico delle informazioni che si conoscono sul sistema software che si vuole creare.

## Referenze