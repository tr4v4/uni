---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 20-10-2023 18:35:45
links:
  - "[[Lecture 20102023135306]]"
  - "[[Lecture 18032024130735]]"
---
# Funzioni continue
---
## Introduzione
Per poter definire quando una funzione è continua dobbiamo avere bene in mente il concetto di [[Punto di accumulazione|punto di accumulazione]] e di [[Punto isolato|punto isolato]].

## Definizione
> Una [[Funzione matematica|funzione]] $f$ si dice **continua** in $x_{0}$ per un insieme $A \subseteq \mathbb{R}^{n}$ (t.c. $x_{0} \in A$) in due casi:
> - $x_{0}$ è un _punto isolato_
> - $x_{0}$ è un _punto di accumulazione_ e $\lim_{x \to x_{0}} f(x) = f(x_{0})$

In particolare capita spesso il secondo caso, per cui la definizione generale che viene data alla continuità per un punto è
$$\lim_{x \to x_{0}} f(x) = f(x_{0})$$
ovvero, per la [[Limite finito al finito di funzione|definizione di limite finito al finito]]
$$\forall \epsilon > 0, \exists \delta > 0: \forall x \in A: 0 < ||x-x_{0}|| < \delta \implies ||f(x)-f(x_{0})|| < \epsilon$$

<u>Nota bene</u>: dell'ipotesi $0 < |x-x_{0}| < \delta$ _in questo caso_ si può anche omettere la diversità $x \neq x_{0}$, riducendola a $|x-x_{0}| < \delta$. Questo perché in primo luogo $x_{0}$ sappiamo essere all'interno del dominio ($A$); ma soprattutto perché se $x=x_{0}$ come conseguenza avremo $|f(x_{0})-f(x_{0})| < \epsilon$ che ovviamente _è sempre vero_.

Si può anche definire la continuità di una funzione per [[Successione numerica|successioni]], ovvero dicendo che $f$ è continua in $x_{0} \in A$ se
$$\forall (x_{k})_{k \in \mathbb{N}} \in \mathbb{R}^{n} : \begin{cases} x_{k} \in A & \forall k \in \mathbb{N} \\ x_{k} \to x_{0} & k \to +\infty \end{cases} \implies f(x_{k}) \stackrel{k \to +\infty}{\longrightarrow} f(x_{0})$$

### Regola
> Ricordare che **la continuità vale solo per i punti del dominio**. Non si può parlare di continuità di un punto per una funzione se questo non appartiene al suo dominio.

Se una funzione risulta continua in tutti i punti del suo dominio, allora, si scrive
$$f: A \to \mathbb{R} \ \text{ continua } \ \forall x \in A \implies f \in C^{0}(A)$$

ovvero la funzione appartiene all'_insieme di tutte le funzioni continue in quel dominio $C^{0}(A)$_[^1] (indicato talvolta come $C(A)$).

Come conseguenza si ha che
> Se una funzione è _continua in tutti i suoi punti del dominio_ allora _per risolvere il limite della funzione per un punto basta calcolare il valore della funzione per quel punto_.

## Funzioni
Delle funzioni elementari abbiamo che:
- _i polinomi sono tutte funzioni continue_ (per questo vale la [[Limite finito al finito di funzione#Polinomio|regola polinomiale per il limite al finito]])
- _tutte le [[Funzioni trigonometriche|funzioni trigonometriche]] sono continue nel loro [[Dominio naturale|dominio naturale]]_[^3]
- _tutte le [[Funzione esponenziale|funzioni esponenziali]] sono continue_
- per le funzioni **incollate** la regolarità dei loro rami è uguale alla regolarità delle funzioni per quei rami, e _bisogna piuttosto concentrarsi sul punto di giunzione_

Un teorema dimostra che tutte le funzioni inverse, _sotto opportune condizioni_, sono continue.

### Composizioni
> Una _composizione di funzioni continue crea una funzione continua_. Il che significa che se si ha una funzione continua $f(x)$ e una funzione continua $g(f(x))$, allora la funzione $x \to g(f(x))$ sarà a sua volta continua.

![[composizione-funzioni-continue.png]]

## Conseguenze
Dall'[[Algebra dei limiti|algebra dei limiti]] si ricava che
$$f(x) \text{ e } g(x) \text{ continue in } x_{0} \implies \begin{cases} f \pm g & \text{continua in } x_{0} \\ c \in \mathbb{R}: c \cdot f & \text{continua in } x_{0} \\ f \cdot g & \text{continua in } x_{0} \\ \frac{f}{g} & \text{continua in } x_{0} \ \ (g(x) \neq 0) \\ |f| & \text{continua in } x_{0} \end{cases}$$[^2]

Le conseguenze fondamentali della continuità sono raccolte in 2 teoremi fondamentali
- [[Teorema degli zeri]]
- [[Teorema di Weierstrass]]

la cui unione fa il [[Teorema di Weierstrass esteso]].

### Limite destro e sinistro
L'[[Limite destro e sinistro di funzione#Osservazione|osservazione sui limiti destri e sinistri]] per quanto riguarda i [[Limite al finito di funzione|limiti al finito]] ovviamente si ripercuote anche sulle funzioni continue, che devono soddisfare una sottospecie di limite finito al finito.

Infatti si ha che
$$\lim_{x \to x_{0}} f(x) = f(x_{0}) \iff \begin{cases} \exists \lim_{x \to x_{0}^{-}} f(x), \lim_{x \to x_{0}^{+}} f(x) \\ \lim_{x \to x_{0}^{-}} f(x) = \lim_{x \to x_{0}^{+}} \\ \lim_{x \to x_{0}^{-}} f(x) = f(x_{0}) = \lim_{x \to x_{0}^{+}} f(x) \end{cases}$$

## Referenze
[^1]: notare che tale insieme ([[Classe C|classe C]]) è di fatto un sottoinsieme dello [[Spazio di funzione|spazio di funzione]] $\mathbb{R}^{A}$, creato con l'[[Assioma di separazione|assioma di separazione]]
[^2]: l'ultima dimostrata con le [[Valore assoluto#Proprietà|proprietà del valore assoluto]]
[^3]: [[Dimostrazione seno funzione continua|dimostrazione seno funzione continua]]