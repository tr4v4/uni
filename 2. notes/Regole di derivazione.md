---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 26-10-2023 23:26:40
links:
  - "[[Lecture 23102023094009]]"
  - "[[Lecture 27102023135003]]"
  - "[[Lecture 30102023093826]]"
---

# Regole di derivazione
---
## Introduzione
### Polinomiali
$$D(x^{n}) = nx^{n-1}$$

$$D(x^{\alpha}) = \alpha x^{\alpha-1} \ \ \ x > 0, \ \alpha \in \mathbb{R}$$

### [[Funzioni trigonometriche|Trigonometriche]]
$$D(\sin(x)) = \cos(x)$$

$$D(\cos(x)) = -\sin(x)$$

$$D(\tan(x)) = \frac{1}{\cos^{2}(x)} = 1 + \tan^{2}(x)$$

## [[Funzioni trigonometriche inverse|Trigonometriche inverse]]
$$D(\arcsin(x)) = \frac{1}{\sqrt{1-x^{2}}} \ \ \ (-1 < x < 1)$$

$$D(\arccos(x)) = - \frac{1}{\sqrt{1-x^{2}}} \ \ \ (-1 < x < 1)$$

$$D(\arctan(x)) = \frac{1}{1 + x^{2}}$$

### [[Funzione esponenziale|Esponenziali]]
$$D(e^{x}) = e^{x}$$

$$D(a^{x}) = \ln(a) \cdot a^x$$

## [[Funzione logaritmica|Logaritmi]]
$$D(\ln(x)) = \frac{1}{x}$$

$$D(\log_{a}(x)) = \frac{1}{\ln(a)} \cdot \frac{1}{x}$$

## Caso speciale
$$D(f(x)^{g(x)}) = D(e^{\ln(f(x)^{g(x)})}) = f(x)^{g(x)} \cdot D(g(x) \cdot \ln(f(x)))$$

Corrisponde all'unione della derivata di una funzione esponenziale con la derivata di una funzione polinomiale.

## Referenze