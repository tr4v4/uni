---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 19-10-2024 18:44:25
links:
  - "[[Lecture 08102024111650]]"
  - "[[Lecture 10102024120505]]"
---
# Grammatiche regolari
---
## Introduzione
> Una [[Grammatiche|grammatica]] è **regolare** $\iff$ ogni _produzione_ è della forma
> $$V \to aW$$
> o
> $$V \to a$$
> dove:
> - $V, W \in NT$, ossia sono _non-terminali_;
> - $a \in T$, ossia è _terminale_.
> 
> Per il _simbolo iniziale_ $S$ è ammessa la produzione $S \to \epsilon$.

<u>Nota bene</u>: in realtà, una definizione più _lasca_, permette produzione $V \to \epsilon$ anche per non-terminali diversi da $S$.

## Teorema
> Il [[Linguaggio generato|linguaggio generato]] da una grammatica regolare $G$ è un [[Linguaggio regolare|linguaggio regolare]], ossia esiste una [[Espressione regolare|espressione regolare]] $s_{G}$ tale che
> $$L(G) = \mathscr{L}[s_{G}]$$
> ovvero che il linguaggio generato da $G$ è lo stesso [[Linguaggio denotato da un'espressione regolare|denotato]] da $s_{G}$.

### Esempi di dimostrazione
#### Caso semplice
Il caso semplice prevede una grammatica $G$ composta da solo _1 non-terminale_. Se per esempio prendiamo la grammatica
$$A \to aA|b|\epsilon$$
è facile intuire che l'espressione regolare associata è
$$a^{*}(b|\epsilon)$$

<u>Nota bene</u>: il linguaggio generato da $G$ e denotato dall'espressione regolare è $L = \{a^{n} | n \geq 0\} \cdot \{b^{n} | n \in \{0, 1\}\}$.

#### Caso medio
Il caso medio invece prevede grammatiche con _2 non-terminali_. In questo caso si passa all'espressione regolare considerando _le produzioni della grammatica come equazioni di un sistema_. Per esempio consideriamo la grammatica
$$A \to aA|bB|c \ \ \ \ \ \ \ \ \ B \to cA|aB|d$$
allora ricaviamo $B$ come una sorta di espressione regolare
$$B \approx a^{*}(cA|d)$$
e a questo punto _sostituiamo_ $B$ dentro la produzione per $A$
$$A \to aA|b(a^{*}(cA|d))|c$$

Quindi considerando le singole sotto-produzioni di $A$ abbiamo
$$A \approx aA|ba^{*}(cA|d)|c$$
e usando le equivalenze delle espressioni regolari arriviamo a
$$aA|ba^{*}(cA|d)|c \approx aA|ba^{*}cA|ba^{*}d|c \approx (a|ba^{*}c)A|ba^{*}d|c$$
e infine, ritrovati nel caso semplice, risolviamo con
$$(a|ba^{*}c)A|ba^{*}d|c \approx (a|ba^{*}c)^{*}(ba^{*}d|c)$$

### Esempi
#### 1.
La grammatica $G$
$$A \to aB|\epsilon \ \ \ \ \ \ \ \ \ B \to bA|\epsilon$$
si scrive in espressione regolare come
$$B \approx (bA|\epsilon) \implies A \approx a(bA|\epsilon)|\epsilon$$
quindi
$$a(bA|\epsilon)|\epsilon \approx abA|a \epsilon|\epsilon \approx (ab)^{*}(a|\epsilon)$$

#### 2.
La grammatica $G$
$$A \to aB|bA|d \ \ \ \ \ \ \ \ \ B \to aB|c$$
diventa in espressione regolare come
$$B \approx a^{*}c \implies A \approx a(a^{*}c)|bA|d$$
quindi
$$a(a^{*}c)|bA|d \approx aa^{*}c|bA|d \approx b^{*}(aa^{*}c|d)$$

<u>Osservazione</u>: la grammatica regolare con un'unica produzione _$A \to aA$ genera il linguaggio vuoto $L = \varnothing$_, perché non termina mai! Di conseguenza _l'espressione regolare associata dev'essere $s_{G} = \varnothing$_.

## Referenze
- [[Equivalenza tra NFA e grammatiche regolari]]
- [[Equivalenza tra DFA e grammatiche regolari]]