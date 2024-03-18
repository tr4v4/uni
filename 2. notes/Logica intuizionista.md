---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 27-12-2023 16:49:54
links:
  - "[[Lecture 05122023161837]]"
---
# Logica intuizionista
---
## Introduzione
> La **logica intuizionista**, frutto dell'[[Intuizionismo|intuizionismo]], si contrappone alla [[Logica classica|logica classica]] in merito all'_approccio nella ricerca della verità_: se per il logico classico bastano _evidenze indirette_ di un fenomeno per considerarlo vero, il logico intuizionista scova invece _evidenze dirette_, prova della formula da dimostrare.

E' fondamentale definire la differenza tra le due evidenze:
> L'evidenza indiretta equivale all'affermazione: "_so che c'è_";
> L'evidenza diretta equivale all'affermazione: "_so chi è_".

Di fatto, prendendo come sintassi la [[Logica del primo ordine|logica del prim'ordine]], si ha che
$$\exists x. P(x)$$
assume due significati diversi a seconda della semantica di riferimento:
- in classica --> so che esiste un $x$ che verifica $P(x)$
- in intuizionista --> so chi è quel $x$ che verifica $P(x)$

## Assunzioni
Ci sono una serie di assunzioni filosofiche che distinguono la logica intuizionista da quella classica:
- l'approccio classico vede la matematica e ogni suo ente come un qualcosa da scoprire, mentre l'**approccio intuizionista come una costruzione artificiale**;
- una dimostrazione in logica classica fornisce una prova di un teorema generale, mentre una **dimostrazione intuizionista fornisce un [[Algoritmo|algoritmo]]** (definito per [[Ricorsione strutturale|ricorsione strutturale]]) **e una dimostrazione in un colpo solo** - di fatto le prove classiche (preferite dai matematici) sono più corte di quelle intuizioniste (preferite dagli informatici);
- la logica classica è [[Teorema di completezza|completa]] sse è aggiunto il **[[Regole di inferenza del RAA|RAA]]**, che invece **non è accettato in intuizionista perché non valido**;
- se nella logica classica il **valore di verità** è determinato e immutabile, **in logica intuizionista è determinato solo quando se ne ha un'evidenza diretta** (un algoritmo);
	- _scopro almeno un algoritmo oppure dimostro che non può esserci_;
	- ciò significa che finché non trovo l'algoritmo _il valore di verità rimane ignoto_;

## Semantiche
Esistono due principali semantiche intuizioniste usate per formalizzare in matematica la mutabilità dei valori di verità:
- [[Semantica di Kripke]]
- [[Semantica di Brouwer-Heyting-Kolmogorov]]

## Corollario
Come conseguenza delle assunzioni e delle semantiche definite, in _logica intuizionista si rifiutano le seguenti [[Tautologia|tautologie]] valide in classica_:
- $\not \Vdash A \lor \neg A$, ovvero non è applicabile [[Regole di inferenza di EM|EM]], per $A$ problema ignoto;
- $\not \Vdash \neg \neg A \implies A$, perché sapendo che non ho un algoritmo con cui dimostrare che non esiste un algoritmo per $A$ non ci dà un algoritmo per $A$;

## Referenze