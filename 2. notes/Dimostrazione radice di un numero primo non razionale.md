---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 29-09-2023 09:48:01
links:
  - "[[Lecture 25092023093433]]"
---
# Dimostrazione radice di un numero primo non razionale
---
## Teorema
Dimostriamo [[Dimostrazione per assurdo|per assurdo]] che $\sqrt{p} \notin \mathbb{Q}$, quindi supponiamo
$$\sqrt{p}=\frac{m}{n}$$
stabilendo che $m$ e $n$ ($\in \mathbb{N}$) siano _coprimi_ tra loro, quindi
$$M.C.D.(m, n) = 1$$
Eleviamo al quadrato ambi i membri per ottenere
$$\frac{m^{2}}{n^{2}} = p$$
$$m^{2}=pn^{2}$$
da cui $p$ è un fattore primo di $m^{2}$, e quindi anche di $m$. Possiamo scrivere allora $m$ come $pm_{1}$, ottenendo
$$(pm_{1})^{2} = pn^{2}$$
$$p^{2}{m_{1}}^{2}=pn^{2}$$
$$\frac{p^{2}}{p}{m_{1}}^{2}=n^{2}$$
$$p{m_{1}}^{2}=n^{2}$$
che significa che $p$ è un fattore primo di $n^{2}$, e quindi anche di $n$.

Ma **se $p$ è fattore primo comune tra $m$ e $n$ allora $M.C.D.(m, n) \neq 1$**, per cui _assurdo_.

## Referenze