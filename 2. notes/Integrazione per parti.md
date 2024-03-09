---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 06-03-2024 19:33:09
links:
  - "[[Lecture 04032024131001]]"
---
# Integrazione per parti
---
## Introduzione
> Per **integrazione per parti** si intende una [[Tecniche d'integrazione|tecnica d'integrazione]] che è una diretta conseguenza della [[Algebra delle derivate#Elementari|derivazione del prodotto]] di due [[Funzione matematica|funzioni]].

Infatti, prese due funzioni $f, g: A \to \mathbb{R}$ e $F$ [[Primitiva|primitiva]] di $f$ su $A$, con $F, f, g$ [[Funzioni continue|continue]], $g$ [[Funzioni derivabili|derivabile]] e $g'$ continua si ha che
$$(F(x)g(x))' = F'(x)g(x) + F(x)g'(x) = f(x)g(x) + F(x)g'(x) \ \ \ \forall x \in A$$

Ora, sfruttando la [[Integrale#Linearità[ 2]|linearità degli integrali]], integro ambo i membri dell'uguaglianza, ottenendo
$$\int (F(x)g(x))' \ dx = \int f(x)g(x) \ dx + \int F(x)g'(x) \ dx$$
che per il [[Teorema fondamentale del calcolo integrale|teorema fondamentale del calcolo integrale]] può essere scritto come
$$F(x)g(x) = \int f(x)g(x) \ dx + \int F(x)g'(x) \ dx$$
o nella più nota forma
$$\int f(x)g(x) \ dx = F(x)g(x) - \int F(x)g'(x) \ dx$$

Questa viene detta **formula d'integrazione per parti**.

<u>Nota bene</u>: _a destra rimane un'integrale_! Per questo non sempre ci aiuta, e questa tecnica _si utilizza solo quando l'integrale rimanente diventa più maneggievole di quello di partenza_.

## Referenze