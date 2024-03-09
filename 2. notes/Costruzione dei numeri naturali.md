---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 04-10-2023 12:18:25
links:
  - "[[Lecture 28092023090721]]"
---
# Costruzione dei numeri naturali
---
## Introduzione
### Preambolo
La teoria [[ZF]] abbiamo detto costituire, attraverso una lista di [[Assioma|assiomi]], le _solide fondamenta della matematica odierna_. Tra di essi, due in particolare consentono di costruire da 0[^1] i [[Numeri naturali|numeri naturali]], o meglio, di **codificarli in insiemistica**: l'[[Assioma del singoletto|assioma del singoletto]] e l'[[Assioma dell'unione|assioma dell'unione]].

Infatti se senza di essi è solo con l'[[Assioma di separazione|assioma di separazione]] che siamo in grado di creare nuovi insiemi (a patto di partire da un altro insieme già esistente), con questi due riusciamo a generare un'infinità di insiemi:
- posso prendere l'_insieme vuoto_ e creare un singoletto contenente tale insieme, e a sua volta un singoletto che contiene il singoletto, quindi un altro singoletto contenente il tutto, in questo modo
  $$\varnothing \to \{\varnothing\} \to \{\{\varnothing\}\} \to \{\{\{\varnothing\}\}\}$$
- posso unire gli insiemi creati tra loro stessi, creando altrettanti insiemi del tipo
  $$\{\varnothing, \{\varnothing\}\} \lor \{\{\varnothing, \{\varnothing\}\}, \varnothing\} \lor \{\{\{\varnothing, \{\varnothing\}\}, \varnothing\}, \{\varnothing, \{\varnothing\}\}\}$$

Tutti questi insiemi hanno in comune il fatto di essere insiemi finiti. Per ora infatti ragioneremo in questi termini.

### Costruzione
Prima di partire con la formazione vera e propria dei numeri naturali per come li conosciamo, è necessario comprendere che **le regole che si andranno a porre saranno descritte dal linguaggio della meta-matematica e della meta-logica**. Useremo, ergo, la matematica per porre le basi alla matematica stessa.

Ora, quindi, avendo in mente già l'idea di numeri naturali senza ancora averli effettivamente inventati, li descriveremo usando la seguente notazione:
$$[[0]] := \varnothing$$
$$[[n + 1]] := [[n]] \cup \{[[n]]\}$$

Come si può notare, quel $n + 1$ è _estremamente meta-matematico_, ma è necessario per descrivere i numeri naturali che a loro volta proveranno la loro stessa definizione!

Si può notare anche il modo in cui vengono sfruttati i due assiomi sopracitati (del singoletto e dell'unione) per codificare ogni numero. Per cui i numeri saranno:
$$[[0]] = \varnothing$$
$$[[1]] = \{\varnothing\}$$
$$[[2]] = \{\varnothing, \{\varnothing\}\}$$
$$[[3]] = \{\varnothing, \{\varnothing\}, \{\varnothing, \{\varnothing\}\}\}$$
e così via...

#### Vantaggi della codifica
A dire la verità, esiste un'infinità di modi per codificare i numeri naturali: **questa è solo la più comoda**. Lo è perché ci basta contare il numero di elementi di ogni insieme per sapere che numero naturale rappresenta[^2]. Ma lo è soprattutto in funzione delle _operazioni matematiche di base_.

Infatti:
- $x < y := x \in y$
- $x \leq y := x \subseteq y$
- $max(x, y) := x \cup y$
- $min(x, y) := x \cap y$

### Diversità
Ho creato i numeri naturali (attenzione, non il loro [[Numeri naturali|insieme]]): **ora devo dimostrare che i numeri siano diversi l'uno dall'altro**. Non posso farlo per tutti, ma con una [[Dimostrazione diversità numeri naturali|coppia di numeri sì]].

## Referenze
[^1]: letteralmente!
[^2]: la famosa [[Cardinalità|cardinalità]]