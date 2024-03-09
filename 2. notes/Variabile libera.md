---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 21-11-2023 21:23:16
links:
  - "[[Lecture 16112023092027]]"
---
# Variabile libera
---
## Introduzione
> Una **variabile libera** in un'espressione in [[Logica del primo ordine|logico del prim'ordine]] è una _variabile non associata ad alcun [[Binder|binder]], e quindi legata ad uno scope globale_ (eventualmente implementato da un'altra espressione più ampia).

## Definizione
E' possibile definire per [[Ricorsione strutturale|ricorsione strutturale]] una funzione[^1] $FV$ (_Free Variables_) che restituisce, di una formula, l'insieme delle variabili libere:
- $FV(c) := \varnothing$
- $FV(x) := \{x\}$
- $FV(f^{n}(t_{1}, t_{2}, t_{3}, ..., t_{n})) := FV(t_{1}) \cup FV(t_{2}) \cup FV(t_{3}) \cup ... \cup FV(t_{n})$
- $FV(P^{n}(t_{1}, t_{2}, t_{3}, ..., t_{n})) := FV(t_{1}) \cup FV(t_{2}) \cup FV(t_{3}) \cup ... \cup FV(t_{n})$
- $FV(\bot) = FV(\top) := \varnothing$
- $FV(\neg P) := FV(P)$
- $FV(P \land Q) = FV(P \lor Q) = FV(P \implies Q) := FV(P) \cup FV(Q)$ 
- $FV(\forall x. P) = FV(\exists x. P) := FV(P) \setminus \{x\}$

<u>Nota bene</u>: il caso interessante è l'ultimo, quello che riguarda i [[Quantificatori|quantificatori]]. Infatti questi sono gli unici che a tutti gli effetti impegnano (_rendono legate_), in quanto binder, delle variabili. Per questo dall'insieme di variabili libere di $P$ bisogna togliere il [[Assioma del singoletto|singoletto]] di $x$ ($\{x\}$).

### Osservazioni
Notare che
$$\text{legata} \neq \neg \text{libera}$$
infatti nella formula
$$P(x) \land \forall x. Q(x)$$
la variabile $x$ è sia libera (per $P(x)$) che legata (per $Q(x)$).

## Referenze
[^1]: funzione intesa come [[Logica del primo ordine#Termini|termine in logica del prim'ordine]]