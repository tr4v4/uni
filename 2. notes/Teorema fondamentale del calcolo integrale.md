---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 27-02-2024 20:52:16
links:
  - "[[Lecture 26022024130925]]"
  - "[[Lecture 28022024141133]]"
---
# Teorema fondamentale del calcolo integrale
---
## Introduzione
> Sia $f: ]a, b[ \to \mathbb{R}$ una [[Funzione matematica|funzione]] [[Funzioni continue|continua]], $c \in ]a, b[$ e $I_{c}: ]a, b[ \to \mathbb{R}$ la [[Funzione integrale|funzione integrale]] di $f$, si ha che $I_{c}$ è [[Funzioni derivabili|derivabile]] $\forall x \in ]a, b[$ e
> $$I'_{c}(x) = f(x) \ \ \ \forall x \in ]a, b[$$
> o, in altre parole
> $$\frac{d}{dx} \int_{c}^{x} f(t) \ dt = f(x) \ \ \ \forall x \in ]a, b[$$
> e che quindi _$I_{c}$ è una [[Primitiva|primitiva]] di $f$_.
> Questo viene detto **primo teorema fondamentale del calcolo integrale**.

### Interpretazione
Il teorema fondamentale del calcolo, oltre a unire i concetti di funzione integrale e primitiva, se considerata su $f(x) \geq 0 \ \ \ \forall x$, ci dice
$$\frac{d}{dx} \text{Area}(A_{x}) = f(x) \ \ \ \forall x > c$$
ovvero che _il rate di crescita dell'area $A_{x}$_, definita in $[c, x]$, _è uguale alla funzione stessa_.

La cosa interessante è che _talvolta è molto complesso calcolare il valore di un integrale_, ma con questo teorema _siamo in grado di conoscere la sua derivata_, e quindi il suo tasso di crescita.

## Dimostrazione
Considero $f: ]a, b[ \to \mathbb{R}$, $c \in ]a, b[$ e $I_{c} : ]a, b[ \to \mathbb{R}$ la funzione integrale di $f$, devo dimostrare
$$I'_{c}(x) = f(x) \ \ \ \forall x \in ]a, b[$$

Calcolo $I'_{c}(x)$ attraverso il [[Derivata#Definizione|rapporto incrementale]], ovvero
$$I'_{c}(x) = \lim_{h \to 0^{+}} \frac{I_{c}(x + h) - I_{c}(x)}{h} = \lim_{h \to 0^{+}} \frac{1}{h} \left(\int_{c}^{x+h} f - \int_{c}^{x} f\right) = \lim_{h \to 0^{+}} \frac{1}{h} \int_{x}^{x+h} f$$

Notiamo quindi che il risultato è una [[Teorema della media integrale|media integrale]] (per $\frac{1}{h}$), perciò sappiamo che
$$\exists c = c(h) \in [x, x+h] : \frac{1}{h} \int_{x}^{x+h} f = f(c)$$

Se il limite è $\lim_{h \to 0^{+}}$ e $c(h) \in [x, x+h]$, ovvero $x \leq c(h) \leq x+h$, per il [[Teorema del confronto|teorema del confronto]] avrò che $c(h) \to x$. Da questo so quindi che
$$\lim_{h \to 0^{+}} \frac{1}{h} \int_{x}^{x+h} f = f(x)$$

Esattamente quello che volevamo dimostrare.

**Qed**.

## Calcolo della derivata dell'integrale
Come già accennato in precedenza, pur non essendo sempre in grado di risolvere un integrale siamo capaci di conoscerne il tasso di crescita, proprio per questo teorema.
In generale abbiamo che date $g: ]a, b[ \to \mathbb{R}$ e $h: \mathbb{R} \to \mathbb{R}$ (derivabile), consideriamo $u(x) = \int_{c}^{h(x)} g(t) \ dt$. Per calcolare $u'(x)$ è necessario considerare la funzione integrale generale $I(z) = \int_{c}^{z} g(t) \ dt$ per cui si ha $I'(z) = \frac{d}{dx} I = g(z)$.

Quindi, $u(x) = I(h(x)) = (I \circ h)(x)$[^1], e per il teorema fondamentale del calcolo vale che $u'(x) = (I \circ h)'(x) = I'(h(x)) \cdot h'(x) = g(h(x)) \cdot h'(x)$, cioè l'applicazione normalissima della _regola della catena_ della derivata.

In definitiva abbiamo
$$\frac{d}{dx} \int_{c}^{h(x)} g(t) \ dt = g(h(x)) \cdot h'(x)$$
(infatti se poniamo $h(x) = x$, quindi come una normale funzione integrale, si ha che il risultato è uguale a $g(x) \cdot 1$, ovvero proprio l'enunciato del teorema)

## Osservazioni
Il teorema assicura che ogni $f: ]a, b[ \to \mathbb{R}$ continua ammette primitive, _il che non significa che le sappia trovare_, ma che _so che esistono_.

## Referenze
- [[Teorema di Torricelli-Barrow]]

[^1]: per la definizione di _funzione composta_