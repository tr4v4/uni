---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 06-03-2024 19:48:24
links:
  - "[[Lecture 04032024131001]]"
  - "[[Lecture 07032024141028]]"
---
# Integrazione per sostituzione
---
## Introduzione
> Per **integrazione per sostituzione** (o **per cambio di variabile**) si intende una [[Tecniche d'integrazione|tecnica d'integrazione]] che prevede di _mutare l'intera [[Integrale|integrale]] sostituendo a un blocco della funzione integranda una funzione sostitutiva_.

Si ha che definite due funzioni $f: A \to \mathbb{R}$ e $h: I \to A$, così che $\exists (f \circ h): I \to \mathbb{R}$ t.c. $(f \circ h)(t) = f(h(t))$, con $f$ [[Funzioni continue|continua]], $h$ [[Funzioni derivabili|derivabile]] e $h'$ continua, allora dati $\alpha, \beta \in I$ vale
$$\int_{h(\alpha)}^{h(\beta)} f(x) \ dx = \int_{\alpha}^{\beta} f(h(t)) h'(t) \ dt$$

<u>Nota bene</u>: $t$ viene integrato in $[\alpha, \beta]$, mentre $x$ in $[h(\alpha), h(\beta)]$.

## Dimostrazione
Per dimostrare questa formula introduco due [[Funzione integrale|funzioni integrali]] $G, H: I \to \mathbb{R}$ tali che
$$G(z) = \int_{\alpha}^{z} f(h(t))h'(t) \ dt$$
$$H(z) = \int_{h(\alpha)}^{h(z)} f(x) \ dx$$

Devo dimostrare
$$G(z) = H(z) \ \ \ \forall x \in I$$

In generale, _per dimostrare l'uguaglianza tra due funzioni basta vedere se hanno lo stesso valore per un certo punto, e se la loro derivata è uguale_. Verifichiamo entrambe le cose.

### $G(\alpha) = H(\alpha)$
Scelgo come punto $\alpha$ perché in questo modo _entrambe le funzioni integrali si calcolano su intervallo degenere_, ovvero su stessi estremi. Questo porta all'uguaglianza
$$G(\alpha) = 0 = H(\alpha)$$

### $G'(z) = H'(z) \ \ \ \forall z \in I$
Calcoliamo singolarmente le [[Teorema fondamentale del calcolo integrale#Calcolo della derivata dell'integrale|derivate degli integrali]], per cui abbiamo
$$G'(z) = \frac{d}{dz} \int_{\alpha}^{z} f(h(t))h'(t) \ dt = f(h(z))h'(z) \ \ \ \forall z \in I$$
e
$$H'(z) = \frac{d}{dz} \int_{h(\alpha)}^{h(z)} f(x) \ dx = f(h(z))h'(z) \ \ \ \forall z \in I$$

per cui
$$G'(z) = H'(z)$$
e di conseguenza le due funzioni sono uguali.

**Qed**.

### Osservazione
Si noti come in realtà questa formula sia un caso speciale dell'[[Integrazione di derivate di funzioni composte|integrazione di derivate di funzioni composte]], e che quindi si possa tranquillamente ricavare da essa.

## Referenze