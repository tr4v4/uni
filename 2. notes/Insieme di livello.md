---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 29-03-2024 15:24:51
links:
  - "[[Lecture 18032024130735]]"
---
# Insieme di livello
---
## Introduzione
> Un **insieme di livello** (o **curva di livello**) $L_{b}$ di una [[Funzione matematica|funzione]] $f$ su un [[Numeri reali|numero reale]] $b$ equivale alla [[Controimmagine|controimmagine]] $f^{-1}(b)$, ovvero
> $$L_{b} = \{x \in A | f(x) = b\} = f^{-1}(b)$$

## Utilizzi
Gli insiemi di livello sono utili per analizzare [[Funzione a più variabili|funzioni a più variabili]]. Graficamente parlando, infatti, fissato un punto $b \in B$ (codominio) l'insieme di livello $f^{-1}(b)$ di una certa funzione $f$ sono tutti quei punti del dominio $x$ per cui $f(x) = b$ che compongono una curva interpretabile come l'intersezione tra la funzione $f$ e un piano $z=b$.

Presa per esempio una funzione $f: \mathbb{R}^{2} \to \mathbb{R}$, l'insieme di livello $f(x, y) = b$ proiettato sul piano cartesiano $x, y$ produce appunto una curva interpretabile come l'intersezione tra $f$ e il piano $z = b$:
$$\begin{cases} f(x, y) \\ z = b \end{cases}$$

![[curve-di-livello-per-il-paraboloide.png]]
![[linee-di-livello-circonferenze.png]]

In generale possiamo dire che una funzione $f: \mathbb{R}^{2} \to \mathbb{R}$ ha delle _curve di livello_ che sono analizzabili per studiare [[Massimo e minimo relativo|punti di massimo o minimo]][^2].

### Esempio
Prendiamo la seguente [[Funzione radiale|funzione radiale]] $f: \mathbb{R}^{2} \to \mathbb{R}$ definita come $f(x, y) = x^{2} + y^{2}$. Studiamo la controimmagine $f^{-1}(b)$ al variare di $b \in \mathbb{R}$:
1. $b < 0 \implies L_{b} = \{(x, y) \in \mathbb{R}^{2} | x^{2}+y^{2} < 0\} = \varnothing$, per cui abbiamo scoperto che $f$ non è mai negativa;
2. $b = 0 \implies L_{b} = \{(x, y) \in \mathbb{R}^{2} | x^{2}+y^{2} = 0\} = \{(0, 0)\}$, per cui abbiamo scoperto che $f$ tocca l'origine solo in un punto, $(0, 0)$;
3. $b > 0 \implies L_{b} = \{(x, y) \in \mathbb{R}^{2} | x^{2}+y^{2} > 0\}$, per cui abbiamo scoperto che $f$ è definita da circonferenze concentriche di raggio $\sqrt{b}$ per $b$ positivi.

<u>Nota bene</u>: _se cammino lungo l'insieme di livello la funzione resta costante_; _se invece mi metto a camminare verso l'interno o verso l'esterno il valore della funzione corrispondente cambia_.

## Referenze
[^2]: dobbiamo immaginare tali curve come le _linee isobare del meteo_, o le _linee che nelle cartine geografiche fisiche definiscono l'altezza delle catene montuose_.