---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 05-10-2023 19:48:28
links:
  - "[[Lecture 02102023093041]]"
---
# Limiti di polinomi
---
## Risoluzioni
### Polinomi
Per risolvere un generico [[Limite di successione|limite]] della forma
$$\lim_{n \to +\infty} n^{4} - 3n^{3} - n$$

è necessario _raccogliere dell'argomento del limite il monomio di grado maggiore_, così da ottenere
$$\lim_{n \to +\infty} n^{4} (1 - \frac{3}{n} - \frac{1}{n^{3}})$$

Ora grazie alle proprietà dell'[[Algebra dei limiti|algebra dei limiti]] risolvendo separatamente il limite per ogni monomio otteniamo
$$+\infty (1 - 0 - 0) = +\infty$$

Per cui
$$\lim_{n \to +\infty} n^{4} - 3n^{3} - n = +\infty$$

### Divisione tra polinomi
Per risolvere un limite della forma
$$\lim_{n \to +\infty} \frac{3n^{2} - 4n^{4}}{6n^{4} - n^{3} - 10}$$

quindi, è necessario fare la stessa operazione che si farebbe con i [[Limiti di polinomi#Polinomi|polinomi]] ma _sia per numeratore che per denominatore_, ottenendo
$$\lim_{n \to +\infty} \frac{n^{4}}{n^{4}} \cdot \frac{\frac{3}{n^{2}} - 4}{6 - \frac{1}{n} - \frac{10}{n^{4}}}$$

Ora siamo in grado di calcolare il limite per ogni termine dell'argomento, per cui arriviamo a dover calcolare
$$1 \cdot -\frac{4}{6} = -\frac{2}{3}$$

Diciamo che per questo caso vale la regola generale
$$
\frac{P(n)}{Q(n)} =
\begin{cases}
\pm \infty & \text{se } degP(n) > degQ(n) \\
l \neq 0 & \text{se } degP(n) = degQ(n) \\
0 & \text{se } degP(n) < degQ(n)
\end{cases}
$$

## Referenze