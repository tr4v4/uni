---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 05-10-2023 19:16:12
links:
  - "[[Lecture 02102023093041]]"
---
# Algebra dei limiti
---
## Introduzione
Prese due [[Successione numerica|successioni]] $a_{n}$ e $b_{n}$ tali per cui
$$a_{n} \longrightarrow l_{1} \ \ , \ \ b_{n} \longrightarrow l_{2}$$
dove
$$l_{1}, l_{2} \in \mathbb{R} \cup \{+\infty\} \cup \{-\infty\}$$

si distinguono le seguenti operazioni tra limiti:
- _addizione/sottrazione_
- _prodotto_
- _divisione_

### Addizione/sottrazione tra limiti
$$
a_{n} + b_{n} =
\begin{cases}
l_{1} + l_{2} & \text{se } l_{1}, l_{2} \in \mathbb{R} \\
+\infty & \text{se } l_{1} = +\infty, l_{2} \in \mathbb{R} \cup \{+\infty\} \text{ (e viceversa)} \\
-\infty & \text{se } l_{1} = -\infty, l_{2} \in \mathbb{R} \cup \{-\infty\} \text{ (e viceversa)}
\end{cases}
$$

La **forma indeterminata** associata alla somma è
$$+\infty -\infty$$

Dal primo caso si ha che
$$\lim_{n \to +\infty} (a_{n} + b_{n}) = \lim_{n \to +\infty} a_{n} + \lim_{n \to +\infty} b_{n}$$

### Prodotto
$$
a_{n} \cdot b_{n} =
\begin{cases}
l_{1} \cdot l_{2} & \text{se } l_{1}, l_{2} \in \mathbb{R} \\
+\infty & \text{se } l_{1} = \pm \infty, l_{2} \in \mathbb{R}_{\pm} \cup \{\pm \infty\} \text{ (e viceversa)} \\
-\infty & \text{se } l_{1} = \pm \infty, l_{2} \in \mathbb{R}_{\mp} \cup \{\mp \infty\} \text{ (e viceversa)}
\end{cases}
$$

La **forma indeterminata** associata al prodotto è
$$\pm \infty \cdot 0$$

### Divisione
Per $b_{n} \neq 0$
$$
\frac{a_{n}}{b_{n}} =
\begin{cases}
\frac{l_{1}}{l_{2}} & \text{se } l_{1}, l_{2} \in \mathbb{R} \land l_{2} \neq 0 \\
+\infty & \text{se } l_{1} = \pm \infty, l_{2} >< 0 \text{ (e viceversa)} \\
-\infty & \text{se } l_{1} = \pm \infty, l_{2} <> 0 \text{ (e viceversa)} \\
0 & \text{se } l_{1} \in \mathbb{R}, l_{2} = \pm \infty
\end{cases}
$$

Le **forme indeterminate** associate alla divisione sono
$$\frac{0}{0}, \frac{\pm \infty}{\pm \infty}, \frac{\pm \infty}{\mp \infty}$$

## Referenze
- [[Forme indeterminate]]