---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 30-11-2023 16:31:57
links:
  - "[[Lecture 29112023131955]]"
  - "[[Lecture 30112023091742]]"
  - "[[Lecture 14122023092114]]"
---
# Algebra astratta
---
## Introduzione
> L'**algebra astratta** (anche chiamata **algebra universale**) è una _branca della matematica che si occupa dello studio delle [[Strutture algebriche|strutture algebriche]]_. E' nata nel XIX secolo per il bisogno di astrazione delle operazioni attuabili sugli [[Insieme|insiemi]]. E' di fatto ciò che **studia in modo sistematico le relazioni tra gli insiemi e le loro operazioni**.

E' parallelizzabile con la geometria, che introduce concetti come _punto_, _retta_ e _piano_ per astrarre proprietà dello spazio così come l'**algebra introduce le strutture algebriche per astrarre proprietà delle operazioni su possibili classi di oggeti**.

### Esempi
Un tipo di algebra astratta sono le [[Algebra di Boole|algebre di Boole]], una struttura algebrica composta da 3 principali operazioni: [[AND]], [[OR]] e [[NOT]]. Esistono una serie di istanze dell'algebra di Boole in campi anche disparati della scienza, come in [[Teoria degli insiemi|teoria degli insiemi]], in [[Logica proposizionale|logica proposizionale]] e nei [[Circuiti combinatori|circuiti combinatori]].

### Requisiti
Per comprendere l'algebra astratta è necessario avere bene a mente i concetti di [[Astrazione|astrazione]] e [[Generalizzazione|generalizzazione]].

I benefici dell'astrazione e della generalizzazione, in particolare nell'informatica, sono:
- _riuso_ - le buone generalizzazione sono riapplicabili
- _chiarezza_ - le generalizzazioni catturano concetti di alto livello, minimizzando le assunzioni
- _decoupling_ - con astrazione e generalizzazione la correttezza di un _modulo_ è indipendente da quello di un altro, permettendo modifiche a se stanti[^1]
- _correttezza_ - senza il riuso l'unica implementazione possibile sarebbe quella del `cut&paste`, spesso portatrice di errori

Sempre in informatica, però, **i [[Linguaggio di programmazione|linguaggi di programmazione]] differiscono molto nella capacità di generalizzazione e astrazione**: per esempio in [[C++]] una funzione che opera su delle [[Liste|liste]] non è generalizzabile su un altro [[ADT|tipo di dato algebrico]]. Non varrebbe infatti per una coppia di naturali, e l'_unica soluzione sarebbe quella di riscrivere la stessa funzione riadattata per poter funzionare con le coppie_; ci sono invece altri linguaggi, in particolare quelli [[Linguaggio di programmazione funzionale|funzionali]] come [[Haskell]], che sono in grado di generalizzare molto bene. **Questa capacità si paga però al prezzo della prestazione**.

## Referenze
- [[Teoria delle categorie]]
- [[Coalgebra]]

[^1]: associabile al concetto di [[Incapsulamento|incapsulamento]]