---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 27-02-2024 19:43:49
links:
  - "[[Lecture 26022024130925]]"
---
# Primitiva
---
## Introduzione
> Sia $f: A \to \mathbb{R}$ dove $A \subseteq \mathbb{R}$, una funzione $F: A \to \mathbb{R}$ si dice **primitiva** di $f$ su $A$ se vale
> $$F'(x) = f(x) \ \ \ \forall x \in A$$
> <u>Nota bene</u>: _la primitiva di una funzione $f$ non è unica, ce ne sono infinite_. Aggiungendo, infatti, una costante $k \in \mathbb{R}$ alla primitiva, essa rimane tale.

Per esempio, considerata $f(x) = \cos{x}$, allora $F(x) = \sin{x}$ è una primitiva di $f$ su tutto $\mathbb{R}$. Ma anche $G(x) = \sin{x} + k$ è una primitiva $\forall k \in \mathbb{R}$.

Per la [[Caratterizzazione delle primitive su un intervallo|caratterizzazione delle primitive su un intervallo]] sappiamo che la costante $k$ è l'unica cosa da cui differiscono due primitive $F$ e $G$ di una funzione $f$ (se lavoriamo su un intervallo).

Ad ogni modo vale che la primitiva è la definizione opposta di [[Derivata|derivata]].

## Primitive fondamentali

| $f(x)$                     | $F(x)$                                                                                                                 |
| -------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| $x^\alpha$                 | $\frac{x^{\alpha+1}}{\alpha+1} + c \ \ \ \forall \alpha \in \mathbb{Z} \setminus \{-1\}, \alpha < 1 \implies x \neq 0$ |
| $e^{x}$                    | $e^{x} + c$                                                                                                            |
| $\frac{1}{x}$              | $\ln{\|x\|} + c \ \ \ \forall x \neq 0$                                                                                |
| $\cos{x}$                  | $\sin{x} + c$                                                                                                          |
| $\sin{x}$                  | $-\cos{x} + c$                                                                                                         |
| $\frac{1}{1+x^{2}}$        | $\arctan{x} + c$                                                                                                       |
| $\frac{1}{\sqrt{1-x^{2}}}$ | $\arcsin{x} + c$                                                                                                       |

### Primitive composte
Spesso e volentieri avviene che si debbano [[Integrazione di derivate di funzioni composte|integrare funzioni composte]], in tal caso si può usufruire della seguente tabella riassuntiva:

| $g(f(x))f'(x)$                    | $G(f(x))$                                                                                                                    |
| --------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| $f(x)^{\alpha} \cdot f'(x)$       | $\frac{f(x)^{\alpha+1}}{\alpha+1} + c \ \ \ \forall \alpha \in \mathbb{Z} \setminus \{-1\}, \alpha < 1 \implies f(x) \neq 0$ |
| $e^{f(x)} \cdot f'(x)$            | $e^{f(x)} + c$                                                                                                               |
| $\frac{f'(x)}{f(x)}$              | $\ln{\|f(x)\|} + c \ \ \ \forall x \neq 0$                                                                                   |
| $\cos{f(x)} \cdot f'(x)$          | $\sin{f(x)} + c$                                                                                                             |
| $\sin{f(x)} \cdot f'(x)$          | $-\cos{f(x)} + c$                                                                                                            |
| $\frac{f'(x)}{1+f(x)^{2}}$        | $\arctan{f(x)} + c$                                                                                                          |
| $\frac{f'(x)}{\sqrt{1-f(x)^{2}}}$ | $\arcsin{f(x)} + c$                                                                                                          |

## Referenze