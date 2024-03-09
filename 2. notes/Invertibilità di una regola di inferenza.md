---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 18-10-2023 20:37:40
links:
  - "[[Lecture 18102023131238]]"
  - "[[Lecture 09112023131356]]"
---
# Invertibilità di una regola di inferenza
---
## Introduzione
Fondamentalmente **una dimostrazione funziona come un labirinto**, per cui si deve spesso e volentieri adoperare quello che in gergo si chiama [[Backtracking|backtracking]]. Non sempre, infatti, nel mondo della [[Deduzione naturale|deduzione naturale]] le [[Regole di inferenza|regole di inferenza]] ti consentono di scegliere _strade dimostrabili_: se la scelta tra due regole ci porta ad una strada sbagliata non possiamo far altro che tornare indietro.

Ebbene esistono però delle _regole che se applicate sono sempre giuste_, e quindi ti evitano di dover tornare indietro: **queste regole si dicono invertibili**.
<u>Attenzione</u>: affinché ciò valga _la tesi di partenza dev'essere dimostrabile_.

## Definizione
> Una regola $F_{1}, F_{2}, F_{3}, ... \Vdash F$ si dice **invertibile** se per ogni $i$ si ha $F \Vdash F_{i}$. Ovvero, se vale la [[Conseguenza logica|conseguenza logica]] tra $F$ e le ipotesi $\Gamma$, allora se è invertibile vale anche tra $\Gamma$ e la tesi $F$.

## Regole invertibili
- "per ogni"
- "implica"
- "and"

## Regole non invertibili
- "or"

## Referenze