---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 29-09-2023 09:23:55
links:
  - "[[Lecture 25092023093433]]"
---
# Dimostrazione radice di 2 non razionale
---
## Teorema
Dimostriamo [[Dimostrazione per assurdo|per assurdo]] che $\sqrt{2} \notin \mathbb{Q}$, quindi supponiamo
$$\sqrt{2} = \frac{m}{n}$$
dove $\exists m, n \in \mathbb{N}$.
Riduciamo ai minimi termini $m$ e $n$, quindi
$$M.C.D.(m, n) = 1$$
per cui $m$ e $n$ sono primi tra loro (_coprimi_).
Eleviamo a 2 ambi i membri
$$\frac{m^{2}}{n^{2}} = 2$$
$$m^{2}=2n^{2}$$
da cui $m^{2}$ è pari, a sua volta dimostrabile che **$m$ è pari**.
Se $m$ è pari allora può anche essere scritto come $m = 2m_{1}$, dove $m_{1} \in \mathbb{N}$. Quindi posso scrivere
$$(2m_{1})^{2}=2n^{2}$$
$$4{m_{1}}^{2}=2n^{2}$$
$$2{m_{1}}^{2} = n^{2}$$
da cui $n^{2}$ è pari, quindi **$n$ è pari**.

Ma **se $m$ e $n$ sono entrambi pari allora il loro $M.C.D. \neq 1$**, per cui _assurdo_.

## Referenze