---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 27-02-2024 21:46:24
links:
  - "[[Lecture 26022024130925]]"
  - "[[Lecture 28022024141133]]"
---
# Teorema di Torricelli-Barrow
---
## Introduzione
> Sia $f: A \to \mathbb{R}$, $F: A \to \mathbb{R}$ [[Primitiva|primitiva]] di $f$, $a, b \in A$, si ha che
> $$\int_{a}^{b} f(x) \ dx = F(b) - F(a) = [F(x)]_{a}^{b}$$
> Questo viene detto **teorema di Torricelli-Barrow**, o anche **secondo teorema fondamentale del calcolo integrale**.

## Dimostrazione
Presa una funzione $f: A \to \mathbb{R}$, fissiamo $c \in A$ così che $I_{c}: A \to \mathbb{R}$ è una [[Funzione integrale|funzione integrale]] di $f$, ovvero $I_{c}(x) = \int_{c}^{x} f$. Per il [[Teorema fondamentale del calcolo integrale|teorema fondamentale del calcolo integrale]] si ha che $I_{c}$ è una primitiva di $f$ su $A$ (infatti $I_{c}'(x) = f(x)$). Ora per la [[Caratterizzazione delle primitive su un intervallo|caratterizzazione delle primitive]], sappiamo che $\exists k \in \mathbb{R} : F(x) = I_{c}(x) + k \ \ \ \forall x \in A$, ovvero che esiste una costante $k$ che distingue la primitiva $I_{c}$ da qualunque altra primitiva di $f$.
Allora prendiamo le due primitive $F(b)$ e $F(a)$, che possiamo scrivere per la relazione sovrastante come $I_{c}(b) + k$ e $I_{c}(a) + k$. La loro differenza viene allora
$$F(b) - F(a) = (I_{c}(b) + k) - (I_{c}(a) + k) = I_{c}(b) - I_{c}(a) = \int_{c}^{b} f - \int_{c}^{a} f = \int_{c}^{b} f + \int_{a}^{c} f = \int_{a}^{b} f$$
ovvero proprio ciò che dovevamo dimostrare.

**Qed**.

## Referenze
- [[Teorema fondamentale del calcolo integrale]]