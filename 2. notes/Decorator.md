---
tags:
  - category/note
  - status/finished
  - topic/ingegneria-del-software
date: 20-10-2025 17:52:52
links:
---
# Decorator
---
## Introduzione
> Il **decorator** è un [[Design patterns strutturali|design pattern strutturale]] simile al [[Composite|composite]] tranne per il fatto che le features sono aggiunte una alla volta ad un singolo componente.

Il suo obiettivo è quello di **aggiungere dinamicamente** (a runtime) **delle responsabilità a un oggetto**. E' un'**alternativa elegante e flessibile al [[Sottotipaggio|sottotipaggio]] per l'estensione delle funzionalità**.

## UML
Si rappresenta attraverso il seguente [[Diagramma delle classi|diagramma delle classi]] [[UML]]:
![[decorator-uml.png]]

Esempio:
![[decorator-example-uml.png]]
```Java
Window w;
w = new ElementaryWindow();
w = new TitledWindow(w, “Title”);
w = new BorderedWindow(w);
```

Questo risparmia tantissima fatica e codice! Infatti se volessimo una finestra con titolo e bordi, dovremmo creare una classe apposita che implementa, magari, quelle due interfacce. Invece, **attraverso il decoratore possiamo unire aspetti diversi di più sottoclassi**.

### Osservazione
Si trova un pattern di [[Ricorsione strutturale|ricorsione strutturale]]:
- il _caso base_ è `ElementaryWindow`;
- il _caso induttivo_ è una qualunque `DecoratedWindow`;

## Referenze