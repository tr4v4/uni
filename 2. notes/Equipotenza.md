---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
  - topic/logica-per-informatica
date: 24-09-2023 15:38:07
links:
  - "[[Lecture 22092023133316]]"
  - "[[Lecture 11102023131154]]"
---
# Equipotenza
---
## Definizione
> Due insiemi $A$ e $B$ si definiscono **equipotenti** quando hanno lo stesso numero di elementi, quindi stessa [[Cardinalità|cardinalità]], ovvero
> $$|A| = |B|$$
> Se esiste una [[Funzione biiettiva|funzione biunivoca]] tra $A$ e $B$ allora essi sono equipotenti, in questo modo:
> $$\exists f: A \to B \text{ biunivoca} \implies |A| = |B|$$

![[insiemi-equipotenti.png]]
Considerazioni:
- la funzione è biunivoca (_invertibilità_)
	- non è lasciato fuori nessun elemento dagli insiemi (_suriettività_)
	- ogni elemento corrisponde ad uno e un solo elemento dell'altro insieme (_iniettività_)

## Regole
### Insiemi finiti
> Un [[Insieme finito|insieme finito]] non può essere equipotente ad un suo sottoinsieme proprio.

### Insiemi infiniti
> Un [[Insieme infinito|insieme infinito]] può essere equipotente ad un suo sottoinsieme proprio.

Questo risulta meno ovvio, ma _nel mondo degli infiniti l'intuizione fa sbagliare_.

Basta infatti che:
- esista una funzione biunivoca tra $A$ e $B$ (infiniti) affinché essi siano equipotenti
- esista una funzione suriettiva tra $\mathbb{N}$ e $A$ (infinito) affinché quest'ultimo sia [[Numerabilità|numerabile]]

## Referenze