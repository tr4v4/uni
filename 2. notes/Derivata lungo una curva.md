---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 03-05-2024 14:22:08
links:
  - "[[Lecture 29042024131336]]"
  - "[[Lecture 02052024141201]]"
---
# Derivata lungo una curva
---
## Introduzione
Abbiamo esteso il concetto di [[Derivata|derivata]] con le [[Derivata parziale|derivate parziali]] fino ad ottenere una versione generalizzata con le [[Derivata direzionale|derivate direzionali]]. Possiamo estendere ancora di più l'idea e _derivare una funzione rispetto a una [[Curva|curva]]_!

## Definizione
> Sia $f: \mathbb{R}^{n} \to \mathbb{R}$ una [[Funzione a più variabili|funzione a più variabili]] [[Funzione differenziabile|differenziabile]], e data una curva $r: ]a, b[ \to \mathbb{R}^{n}$ [[Funzioni derivabili|derivabile]], allora la [[Funzione composta|funzione composta]] $(f \circ r): ]a, b[ \to \mathbb{R}$ è derivabile, _la sua derivata identifica la derivata di $f$ lungo $r$_ e si ha
> $$(f \circ r)'(t) = \frac{\partial}{\partial t}(f \circ r)(t) = \frac{\partial}{\partial t}(f(r(t))) = <\nabla f(r(t)), r'(t)>$$
> <u>Nota bene</u>: è una _versione del [[Teorema del gradiente|teorema del gradiente]] ma per derivate rispetto a una curva, e non una direzione_.

### Dimostrazione
Assumendo che $f$ sia differenziabile, possiamo allora sviluppare Taylor al 1° ordine, ottenendo (con $h = x - \bar{x}$)
$$f(\bar{x} + h) = f(\bar{x}) + <\nabla f(\bar{x}), h> + o(||h||)$$

Allo stesso modo, assumendo $r$ derivabile ed essendo il dominio di $r$ $]a, b[ \subseteq \mathbb{R}$, ho che $\text{derivabilità} \iff \text{differenziabilità}$, e quindi che posso sviluppare Taylor al 1° ordine, ottenendo
$$r(\bar{t} + h) = r(\bar{t}) + r'(\bar{t}) \cdot h + o(h)$$

Dati i due sviluppi precedenti, devo dimostrare che
$$(f \circ r)'(t) = <\nabla f(r(t)), r'(t)>$$
Uso la definizione di derivata, ovvero il limite del rapporto incrementale, per definire $(f \circ r)'(t)$:
$$(f \circ r)'(t) = \lim_{s \to 0} \frac{f(r(t + s)) - f(r(t))}{s}$$
allora sostituisco lo sviluppo di $r(t + s)$ (con $h = s$), e ottengo
$$(f \circ r)'(t) = \lim_{s \to 0} \frac{f(r(t) + r'(t) \cdot s + o(s)) - f(r(t))}{s}$$

Ora, considero $\bar{x} = r(t)$ e $h = r'(t) \cdot s + o(s)$, e sostituisco lo sviluppo di $f(\bar{x} + h)$:
$$(f \circ r)'(t) = \lim_{s \to 0} \frac{f(r(t)) + < \nabla f(r(t)), r'(t) \cdot s + o(s)> + o(||r'(t) \cdot s + o(s)||) - f(r(t))}{s}$$

semplificando viene:
$$(f \circ r)'(t) = \lim_{s \to 0} \left(\frac{<\nabla f(r(t)), r'(t) \cdot s + o(s)>}{s} + \frac{o(||r'(t) \cdot s + o(s)||)}{s}\right)$$

ora, il primo membro del limite, per le proprietà del [[Prodotto scalare|prodotto scalare]], si può scomporre in
$$<\nabla f(r(t)), r'(t) \cdot s + o(s)> = s <\nabla f(r(t)), r'(t)> + <\nabla f(r(t)), o(s)>$$

Per cui il limite diventa
$$(f \circ r)'(t) = \lim_{s \to 0} \left(\frac{s <\nabla f(r(t)), r'(t)>}{s} + \frac{<\nabla f(r(t)), o(s)>}{s} + \frac{o(||r'(t) \cdot s + o(s)||)}{s}\right)$$

I due ultimi membri del limite, per $s \to 0$, tendono a 0, per cui rimane il primo membro, che di fatto viene
$$(f \circ r)'(t) = \lim_{s \to 0} \frac{s <\nabla f(r(t)), r'(t)>}{s} = < \nabla f(r(t)), r'(t) >$$

**Qed**.

## Calcolo
Per calcolare la derivata rispetto a una curva possiamo agire in 2 modi:
1. calcolare la derivata della funzione composta, ovvero $\frac{\partial}{\partial t}(f \circ r)$;
2. usare la formula del gradiente esposta nella definizione, ovvero $<\nabla f(r(t)), r'(t)>$.

### Esempio
Data la funzione $f(x, y) = xy + \sin{y^{2}}$ e la curva $r(t) = (e^{t}, 2e^{t})$ calcoliamo la derivata di $f$ lungo $r$ con entrambi i modi.

#### 1.
$$\frac{\partial}{\partial t}(f \circ r) = \frac{\partial}{\partial t}(2e^{2t} + \sin{4e^{2t}}) = 4e^{2t} + 8e^{2t}\cos{4e^{2t}}$$

#### 2.
$$\nabla f(x, y) = (y, x + 2y\cos{y^{2}}) \implies \nabla f(r(t)) = (2e^{t}, e^{t}+4e^{t}\cos(4e^{2t}))$$
$$r'(t) = (e^{t}, 2e^{t})$$
$$<\nabla f(r(t)), r'(t)> = 4e^{2t} + 8e^{2t}\cos{4e^{2t}}$$

### Esempio
Data $f: \mathbb{R}^{2} \to \mathbb{R}$ differenziabile, poniamo $h(t, s) = f(t^{2}s, \sin{ts^{2}})$. Dobbiamo calcolare $\frac{\partial h}{\partial t}$ e $\frac{\partial h}{\partial s}$.

Per calcolare $\frac{\partial h}{\partial t}$ considero $h(t, s) = f(r(t))$ dove $r(t) = (t^{2}s, \sin{ts^{2}})$, perché fondamentalmente $s$ diventa costante visto che sto derivando rispetto a $t$.

Allora $r'(t) = (\partial_{t} t^{2}s, \partial_{t} \sin{ts^{2}}) = (2ts, s^{2}\cos{ts^{2}})$ e $\frac{\partial h}{\partial t}(t, s) = (f \circ r)'(t) = <\nabla f(t^{2}s, \sin{ts^{2}}), (2ts, s^{2}\cos{ts^{2}}) >$.

Invece per $\frac{\partial h}{\partial s}$ rimane invariato $\nabla f(t^{2}s, \sin{ts^{2}})$ e cambia $r'(s) = (t^{2}, 2ts\cos{ts^{2}})$. Come risultato si ha $\frac{\partial h}{\partial s} (t, s) = (f \circ r)'(t) = <\nabla f(t^{2}s, \sin{ts^{2}}), (t^{2}, 2ts\cos{ts^{2}})>$.

## Referenze