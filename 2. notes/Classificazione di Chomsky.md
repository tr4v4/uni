---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 16-08-2025 21:52:44
links:
  - "[[Lecture 22102024110521]]"
---
# Classificazione di Chomsky
---
## Introduzione
> Per **classificazione di Chomsky** si intende la classificazione delle [[Grammatiche|grammatiche]], dei [[Linguaggio formale|linguaggi]] e degli [[Automa|automi]] associati.

## Classificazione
### Grammatiche
![[classificazione-grammatiche.png]]

Nella fattispecie:
- [[Grammatiche regolari]]
	- $A \to aB$
	- $A \to a$
	- $S \to \epsilon$
- [[Grammatiche libere]] (dal contesto)
	- $A \to \gamma$ con $\gamma \in (NT \cup T)^{+}$
	- $S \to \epsilon$
- [[Grammatiche dipendenti dal contesto]]
	- $\gamma A \delta \to \gamma w \delta$ con $\gamma, \delta \in (NT \cup T)^{*}$ e $w \in (NT \cup T)^{+}$
	- $S \to \epsilon$
- [[Grammatiche monotone]]
	- $\gamma \to \delta$ con $|\gamma| \geq |\delta|$
- [[Grammatiche generali]] (o a struttura di frase)
	- $\gamma \to \delta$

### Linguaggi
![[classificazione-linguaggi.png]]

<u>Nota bene</u>: il motivo per cui i linguaggi dipendenti e monotoni coincidono è perché esiste un teorema che afferma che per ogni $G_{1}$ monotona, esiste $G_{2}$ dipendente dal contesto tale che $L(G_{1}) = L(G_{2})$.

### Automi
![[classificazione-automi.png]]

Gli automi limitati:
- leggono e scrivono sul nastro;
- si muovono a destra e a sinistra;
- riconoscono per stato finale;
- hanno spazio utilizzabile limitato dalla lunghezza dell'input;

Gli automi di Turing sono le [[Macchina di Turing|macchine di Turing]]: automi limitati ma senza vincoli di spazio (il nastro è teoricamente infinito).

## Referenze