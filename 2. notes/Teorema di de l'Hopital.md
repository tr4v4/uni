---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 12-11-2023 15:07:09
links:
  - "[[Lecture 10112023134301]]"
---
# Teorema di de l'Hopital
---
## Introduzione
> Il **teorema di de l'Hopital**, composto da una serie di sottoteoremi, afferma che fissate due funzioni $f(x)$ e $g(x)$, e un punto $x_{0} \in \stackrel{°}{I} \cup \{\pm \infty\}$ ([[Punto interno|punto interno]] del dominio o $\pm$ infinito), sotto le ipotesi
> 1. $f(x)$, $g(x)$ funzioni [[Funzioni continue|continue]]
> 2. $f(x_{0}) = g(x_{0}) = 0 \cup \{\pm \infty\}$
> 3. $f(x)$, $g(x)$ funzioni [[Funzioni derivabili|derivabili]] in $I \setminus \{x_{0}\}$
> 4. $g'(x) \neq 0$ per $x \in I \setminus \{x_{0}\}$
> 5. $\exists \lim_{x \to x_{0}} \frac{f'(x)}{g'(x)} = l \in \mathbb{R} \cup \{\pm \infty\}$
> 
> avviene che
> $$\lim_{x \to x_{0}} \frac{f(x)}{g(x)} = \lim_{x \to x_{0}} \frac{f'(x)}{g'(x)}$$

<u>Nota bene</u>: c'è un'altra ipotesi che si omette perché ricavabile dalle altre, ovvero $g(x) \neq 0$ in $x \in I \setminus \{x_{0}\}$. Anche senza metterla, infatti, se avessimo un punto $\bar{x} \neq x_{0}$ che annulla $g(\bar{x})$, allora per il [[Teorema di Rolle|teorema di Rolle]] avremmo che esiste almeno un punto $c$ tra $\bar{x}$ e $x_{0}$ che annulla la derivata $g'(c)$. Ma questo è in contraddizione con la 4° ipotesi $g'(x) \neq 0$ per $x \in I \setminus \{x_{0}\}$.

## Dimostrazione
Dimostriamo il teorema prendendo in considerazione solo il caso in cui $\frac{f(x_{0})}{g(x_{0})} = \frac{0}{0}$.

Supponendo
$$\lim_{x \to x_{0}}\frac{f'(x)}{g'(x)} = l$$
vogliamo dimostrare che
$$\lim_{x \to x_{0}^{+}} \frac{f(x)}{g(x)} = l = \lim_{x \to x_{0}^{-}} \frac{f(x)}{g(x)}$$

### $\lim_{x \to x_{0}^{+}} \frac{f(x)}{g(x)} = l$
Costruiamo il [[Limite formulato per successione|limite per successione]], supponendo quindi che
$$\forall x_{n} : x_{0} < x_{n} \ \ \forall n, \ \ x_{n} \stackrel{n \to +\infty}{\longrightarrow} x_{0} \implies \frac{f(x_{n})}{g(x_{n})} \stackrel{n \to +\infty}{\longrightarrow} \frac{f(x_{0})}{g(x_{0})}$$
vogliamo dimostrare
$$\lim_{n \to +\infty} \frac{f(x_{n})}{g(x_{n})} = l$$

Ora, dalle ipotesi del teorema sappiamo che $f(x_{0}) = g(x_{0}) = 0$, per cui
$$\frac{f(x_{n})}{g(x_{n})} = \frac{f(x_{n}) - f(x_{0})}{g(x_{n}) - g(x_{0})}$$
Sapendo che $f(x)$ e $g(x)$ sono continue in $[x_{0}, x_{n}]$ e derivabili in $]x_{0}, x_{n}[$, e soprattutto che $g'(x)$ non si annulla nell'intervallo (dalle ipotesi del teorema), possiamo applicare [[Teorema di Cauchy|Cauchy]], e sapere come conseguenza che
$$\exists c \in ]x_{0}, x_{n}[ : \frac{f(x_{n}) - f(x_{0})}{g(x_{n}) - g(x_{0})} = \frac{f'(c)}{g'(c)}$$

Sappiamo quindi che tra $x_{0}$ e $x_{n}$ esiste un $c$ che rende vera l'uguaglianza. Ma per il [[Teorema del confronto|teorema del confronto]], per $n \to +\infty$ si ha che
- $x_{0} \to x_{0}$
- $x_{n} \to x_{0}$, per le ipotesi del limite per successione

per cui di conseguenza, $c$ schiacciato dalle due successioni dovrà tendere anch'esso a $x_{0}$:
$$c_{n} \stackrel{n \to +\infty}{\longrightarrow} x_{0}$$

Ora, per l'ultima ipotesi del teorema sappiamo che
$$\exists \lim_{x \to x_{0}} \frac{f'(x)}{g'(x)} = l$$
che unita alla teorema del limite per successione ci porta a
$$\lim_{n \to +\infty} \frac{f'(c_{n})}{g'(c_{n})} = l$$

Abbiamo quindi
$$\frac{f(x_{n})}{g(x_{n})} = \frac{f(x_{n}) - f(x_{0})}{g(x_{n}) - g(x_{0})} = \frac{f'(c)}{g'(c)} \stackrel{n \to +\infty}{\longrightarrow} l$$

da cui
$$\lim_{n \to +\infty} \frac{f(x_{n})}{g(x_{n})} = l$$
che è equivalente a dire
$$\lim_{x \to x_{0}^{+}} \frac{f(x)}{g(x)} = l$$
**Qed**.

### $\lim_{x \to x_{0}^{-}} \frac{f(x)}{g(x)} = l$
Analoga alla dimostrazione di prima.

## Osservazione
Il teorema afferma che **se esiste il limite del rapporto delle derivate allora esiste il limite del rapporto delle funzioni, non viceversa**.

Il rapporto è di tipo [[Implicazione|implicativo]], per cui può capitare che per alcune funzioni esista il limite del rapporto delle funzioni ma non quello delle derivate.

Si prenda come esempio di riferimento la funzione:
$$f(x) = \begin{cases} x^{2} \cdot \sin\left(\frac{1}{x}\right) & x \neq 0 \\ 0 & x = 0 \end{cases}$$
$$g(x) = x$$

## Utilizzo
Nella pratica il teorema di Hopital si utilizza _senza verificare il limite del rapporto delle derivate_: se il limite, di una $n$-esima derivazione, non dovesse esistere, allora vorrebbe dire che Hopital non era applicabile sin dall'inizio.

Un trucco d'applicazione per i casi in cui si ha, per esempio, una [[Forme indeterminate|forma indeterminata]] $0 \cdot \infty$, è di _invertire il termine a $0$ e porlo al denominatore_, così da ritrovarsi $\frac{\infty}{\frac{1}{0}}$, sbloccabile con Hopital.

<u>Attenzione</u>: Hopital è applicabile sia per la forma indeterminata $\frac{0}{0}$ che $\frac{\infty}{\infty}$, ma non sempre porta a una semplificazione del limite. Quindi quando ci si vuole ricondurre a una forma sbloccabile con Hopital _fare attenzione a scegliere quella corretta_.

Nonostante ciò, Hopital non è lo strumento migliore per risolvere limiti complessi, perché anzi rischia, per via della [[Comandi iterativi|reiterazione]] della derivazione delle funzioni, di far incorrere in errori[^1].

## Referenze
[^1]: per questo sono usati gli [[Sviluppo in serie di Taylor|sviluppi in serie di Taylor]]