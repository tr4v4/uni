---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 30-09-2024 20:17:29
links:
  - "[[Lecture 24092024110820]]"
---
# Grammatiche libere
---
## Introduzione
> Una **grammatica libera** (**da contesto**) è una [[Grammatiche|grammatica]] definita dalla _quadrupla_
> $$(NT, T, S, R)$$
> dove:
> - $NT$ è un insieme finito di **simboli non terminali**, di solito indicati con lettere maiuscole
> - $T$ è un insieme finito di **simboli terminali**, di solito indicati con lettere minuscole
> - $S$ ($\in NT$) è il **simbolo iniziale**
> - $R$ è un insieme finito di **produzioni** (o regole) della forma $V \to v : V \in NT \land v \in (T \cup NT)^{*}$

### Esempi
#### 1
La grammatica
$$G = (\{S\}, \{a, b, +, *\}, S, R)$$
con
$$R = \{S \to a, S \to b, S \to S+S, S \to S*S\}$$

è quella che [[Rappresentazione finita di un linguaggio|rappresenta finitamente]] il [[Linguaggio formale|linguaggio]] che contiene tutte le espressioni aritmetiche formate da variabili $a$ e $b$, dagli operatori $*$ e $+$.

Si riassume nella notazione standard delle grammatiche come
$$S \to a|b|S+S|S*S$$

#### 2
Un'altra grammatica è
$$G = (\{S, A\}, \{a, b\}, S, R)$$
con
$$R = \{S \to aAb, A \to aAb, A \to \epsilon\}$$

O più semplicemente
$$\begin{align}
& S \to aAb \\
& A \to aAb|\epsilon
\end{align}$$

#### 3
Definiamo ora le due seguenti grammatiche:
$$\begin{align}
& E \to I|E+E|E*E|-E|(E) \\
& I \to a|b|Ia|Ib
\end{align}$$
Ora, è facile capire che il **linguaggio generato** da $I$ è l'insieme di tutte le possibili sequenze non vuote di $a$ e $b$:
$$L(I) = \{a, b\}^{+}$$

Invece, il linguaggio generato da $E$ non è che l'insieme delle espressioni aritmetiche costruite sugli identificatori ($L(I)$).

## Referenze
- [[Derivazione]]
- [[Linguaggio generato]]