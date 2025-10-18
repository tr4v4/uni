---
tags:
  - category/note
  - status/finished
  - topic/programmazione
  - topic/linguaggi-di-programmazione
date: 03-12-2023 17:01:28
links:
  - "[[Lecture 29112023092601]]"
  - "[[Lecture 14052025105842]]"
---
# Costruttore
---
## Introduzione
> Il **costruttore**, nell'ambito della [[OOP|programmazione a oggetti]], è uno speciale metodo di una [[Classe|classe]] che inizializza i suoi attributi nella fase di creazione di un [[Oggetto|oggetto]].
> Piu' precisamente, accetta dei parametri e restituisce l'oggetto istanziato con essi.

## Caratteristiche
<u>Nota bene</u>:
- nella maggior parte dei [[Linguaggio di programmazione|linguaggi di programmazione]] odierni, **il costruttore deve avere lo stesso nome della classe**;
- **il costruttore non ha un tipo di ritorno**
- **non è possibile invocare il costruttore come gli altri metodi**

### Ereditarieta'
Chiaramente, se il linguaggio supporta l'[[Ereditarietà|ereditarieta']] allora bisogna ricordarsi di inizializzare anche i dati della superclasse!

Di solito, linguaggi come [[C++]] e [[Java]] impongono che il costruttore di una classe chiami prima il costruttore della superclasse (_concatenamento di costruttori_).

### Overloading
Il costruttore, inoltre, puo' essere soggetto a [[Overloading|overloading]], e segue le stesse regole dei metodi sovraccaricati (_static dispatch_).

## Referenze