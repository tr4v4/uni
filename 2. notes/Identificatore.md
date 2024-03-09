---
tags:
  - "#category/note"
  - "#status/finished"
  - topic/programmazione
date: 20-09-2023 19:23:18
links:
  - "[[Lecture 20092023091613]]"
  - "[[Lecture 10102023093258]]"
  - "[[Lecture 11102023092734]]"
---
# Identificatore
---
## Definizione
> Un **identificatore** (anche più comunemente chiamato _variabile_) è un nome simbolico/logico a cui viene assegnato un valore (modificabile nel tempo) associato a una [[RAM|locazione di memoria]].

Il motivo per cui si usano gli identificatori e non direttamente gli indirizzi di memoria per riferirci ai valori salvati in RAM è perché **non possiamo sapere a priori in quali locazioni di memoria verrà caricato il programma**. Ricordiamo infatti che è compito del [[Loader|loader]] (in fase di esecuzione) di caricare il programma in RAM.

Il contenuto di un identificatore, e quindi di una locazione di memoria, può variare nel corso d'esecuzione del programma **purché sia rispettato il loro tipo**. Da questo le _variabili informatiche_ si discostano dalle _variabili matematiche_.

## Regola
Gli identificatori possono essere formati da:
- lettere
- cifre
- \_

Non possono invece:
- contenere spazi
- essere parole chiave (come `int`, `float`, `double`, `main`, `while`)

<u>Attenzione</u>: C++ **è case sensitive**.

## Tipologie
Di variabili ne esistono di due principali tipi, a seconda del loro [[Scope|scope]]:
- _locali_ --> ogni identificatore posto all'interno di un blocco, per cui vale solo all'interno di esso
- _globali_ --> ogni identificatore posto al di fuori di qualsiasi blocco, per cui vale per ogni altro blocco del programma

## Referenze