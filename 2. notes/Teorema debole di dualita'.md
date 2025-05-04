---
tags:
  - category/note
  - status/finished
  - topic/ottimizzazione-combinatoria
date: 21-04-2025 21:34:20
links:
  - "[[Lecture 14042025091835]]"
  - "[[Lecture 16042025091309]]"
---
# Teorema debole di dualita'
---
## Introduzione
> Il **teorema debole di dualità** della [[Teoria della dualita'|teoria della dualita']] afferma che se $\bar{x}, \bar{y}$ sono una soluzione ammissibile rispettivamente del primale e del duale, allora
> $$c\bar{x} \leq \bar{y}b$$

## Dimostrazione
Nel caso della coppia asimmetrica si ha che:
$$\begin{cases} A\bar{x} \leq b \\ \bar{y}A = c, \bar{y} \geq 0 \end{cases} \implies \begin{cases} \bar{y}A\bar{x} \leq \bar{y}b \\ \bar{y}A\bar{x} = c\bar{x} \end{cases} \implies c\bar{x} \leq \bar{y}b$$

Nel caso della coppia simmetrica si ha che:
$$\begin{cases} A\bar{x} \leq b, \bar{x} \geq 0 \\ \bar{y}A \geq c, \bar{y} \geq 0 \end{cases} \implies \begin{cases} \bar{y}A\bar{x} \leq \bar{y}b \\ \bar{y}A\bar{x} \geq c\bar{x} \end{cases} \implies c\bar{x} \leq \bar{y}b$$

**Qed**.

## Corollario
### Illimitato - vuoto
> Se il primale e' illimitato, allora il duale e' vuoto.

#### Dimostrazione
Se il primale e' illimitato, allora $\forall M \in \mathbb{R}$ esiste una soluzione ammissibile $x$ per il primale tale che $cx > M$; se per assurdo esistesse una soluzione ammissibile $y$ per il duale, allora troveremmo un $x$ ammissibile per il primale tale che $cx > yb$, in assurdo per il teorema debole di dualità.

**Qed**.

### Uguaglianza $\implies$ ottimo
> Se $\bar{x}$ e $\bar{y}$ sono soluzioni ammissibili per primale e duale, e $c\bar{x} = \bar{y}b$, allora $\bar{x}, \bar{y}$ sono soluzioni ottime[^1].

#### Dimostrazione
Se per assurdo $\bar{x}, \bar{y}$ non fossero ottime, allora esisterebbe un $x$ ammissibile per il primale tale che $cx > c\bar{x}$; ma allora $cx > c\bar{x} = \bar{y}b$, il che e' assurdo per il teorema debole di dualità.

**Qed**.

## Referenze

[^1]: e' lo stesso ragionamento del [[Teorema max-flow min-cut|teorema max-flow min-cut]]!
