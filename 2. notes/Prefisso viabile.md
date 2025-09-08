---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 28-08-2025 12:01:13
links:
---
# Prefisso viabile
---
## Introduzione
> Un **prefisso viabile** e' una sequenza $\in (T \cup NT)^{*}$ di una [[Grammatiche|grammatica]] che puo' apparire sulla pila di un [[Parser bottom-up|parser bottom-up]] _per una computazione che accetta un input_.
> In altri termini, e' _necessario che sul top della pila compaia un prefisso di una parte destra di una produzione_.
> Formalmente, su $G$ [[Grammatiche libere|grammatica libera]], una stringa $\gamma \in (T \cup NT)^{*}$ e' un prefisso viabile per $G$ $\iff$ esiste una [[Derivazione canonica destra|derivazione canonica destra]]
> $$S \implies^{*} \delta A y \implies \delta \alpha \beta y = \gamma \beta y$$
> per qualche $y \in T^{*}, \delta \in (T \cup NT)^{*}$ e per una produzione $A \to \alpha \beta$.

Inoltre:
- $S$ e' un prefisso viabile per definizione;
- un prefisso viabile e' **completo** se $\beta = \epsilon$, e in tal caso $\alpha$ e' detta **maniglia** (**handle**) per $\gamma y$ --> in cima alla pila trovo $\alpha^{R}$ e posso fare una _reduce_.

Allora ridurre a zero il nondeterminismo di un parser bottom-up, eliminando i conflitti shift-reduce e reduce-reduce, e' equivalente a:
- _riconoscere le maniglie sulla cima della pila e ridurle_;
- _scegliere, tra piu' riduzioni, solo quelle che producono sulla pila un nuovo prefisso viabile_;
- _scegliere spostamenti (shift) che completino i prefissi viabili sulla pila e facciano comparire una nuova maniglia_;

## Teoremi
### Regolarita'
> Data $G$ grammatica libera, i prefissi viabili di $G$ costituiscono un [[Linguaggio regolare|linguaggio regolare]], che puo' essere descritto da un [[DFA]].

Questo teorema consente di costruire proprio il [[DFA dei prefissi viabili]].

## Referenze