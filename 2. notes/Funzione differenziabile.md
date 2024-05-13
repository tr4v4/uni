---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 29-03-2024 18:12:21
links:
  - "[[Lecture 21032024140949]]"
  - "[[Lecture 27032024141122]]"
  - "[[Lecture 04042024140958]]"
  - "[[Lecture 08042024130916]]"
---
# Funzione differenziabile
---
## Introduzione
> Una [[Funzione matematica|funzione]] $f: \mathbb{R}^{n} \to \mathbb{R}$ ([[Funzione a più variabili|a più variabili]]) si dice **differenziabile** in $\bar{x_{0}} \in \mathbb{R}^{n}$ se:
> 1. $\exists \partial_{k}f(\bar{x_{0}}) \ \ \ \forall k \in \{1, \cdots, n\}$, ovvero esistono le derivate parziali;
> 2. vale lo sviluppo $f(\bar{x_{0}} + \bar{h}) = f(\bar{x_{0}}) + \nabla f(\bar{x_{0}}) \cdot \bar{h} + o(||\bar{h}||)$ per $\bar{h} \in \mathbb{R}^{n}: \bar{h} \to \underline{0}$ (dove $\nabla f(\bar{x}) \cdot \bar{h}$ è il [[Prodotto scalare|prodotto scalare]] tra il [[Gradiente|gradiente]] di $f$ in $\bar{x_{0}}$ e $\bar{h}$), ovvero se si può [[Sviluppo in serie di Taylor|sviluppare Taylor]] al 1° ordine su $\bar{x_{0}}$[^1].

Equivalentemente possiamo scrivere lo sviluppo usando $\bar{x} = \bar{x_{0}} + \bar{h}$, per cui viene
$$f(\bar{x}) = f(\bar{x_{0}}) + \nabla f(\bar{x_{0}}) \cdot (\bar{x} - \bar{x_{0}}) + o(||\bar{x} - \bar{x_{0}}||)$$
che è la versione da cui possiamo identificare il _polinomio di Taylor_ $f(\bar{x}) + \nabla f(\bar{x}) \cdot (\bar{t} - \bar{x})$.

### In $\mathbb{R}^{2}$
In $\mathbb{R}^{2}$ si ha che $\nabla f(x_{0}, y_{0}) = (\partial_{x}f(x_{0}, y_{0}), \partial_{y}f(x_{0}, y_{0}))$, per cui il polinomio di Taylor al 1° ordine che _approssima_ una funzione $f: \mathbb{R}^{2} \to \mathbb{R}$ in un punto $(x_{0}, y_{0}) \in \mathbb{R}^{2}$ è
$$T_{1}(x, y) = f(x_{0}, y_{0}) + (\partial_{x}f(x_{0}, y_{0}), \partial_{y}f(x_{0}, y_{0})) \cdot (x-x_{0}, y-y_{0})$$

che è quindi uguale a, sviluppando il prodotto scalare,
$$T_{1}(x, y) = f(x_{0}, y_{0}) + \partial_{x}f(x_{0}, y_{0}) \cdot (x-x_{0}) + \partial_{y}f(x_{0}, y_{0}) \cdot (y-y_{0})$$

Se Taylor al 1° ordine approssima una funzione $g: \mathbb{R} \to \mathbb{R}$ in un punto $x_{0}$ come la retta tangente a $g(x_{0})$, **in $\mathbb{R}^{2}$ il polinomio $T_{1}(x, y)$ è il [[Grafico di una funzione|grafico]] del [[Piano tangente|piano tangente]] a $f$ per il punto $f(x_{0}, y_{0})$**.

## Esercizio
Per comprendere la differenziabilità commentiamo un esercizio riassuntivo, fondamentale per capire a fondo il [[Rapporto tra derivabilità e differenziabilità|rapporto tra derivabilità e differenziabilità]].

Ci viene chiesto di $f(x, y) = \sqrt{|x|}\sqrt{|y|}$ _per quali $(\bar{x}, \bar{y}) \in \mathbb{R}^{2}$ esistono $\partial_{x}f$ e $\partial_{y}f$, e in quali di questi $f$ è differenziabile_. Scopriremo che **per certi punti la funzione sarà derivabile MA non differenziabile**.

### $\exists \partial_{x}f, \partial_{y}f$
Per verificare l'esistenza di queste derivate parziali bisognerebbe usare la loro definizione formale: il _limite del rapporto incrementale_. Ma da calcolare viene troppo complesso... Allora ci concentriamo sull'analisi dei punti critici di $f$, ovvero $(0, 0)$. Analizzeremo quindi le 4 combinazioni possibili.

#### Caso A: $\bar{x} \neq 0 \land \bar{y} \neq 0$
Il caso è triviale, perché sappiamo che $\sqrt{|x|}\sqrt{|y|}$ è _composizione di funzioni elementari_, per cui per $x \neq 0 \neq y$ si ha che $\exists \partial_{x}f$ e $\exists \partial_{y}f$.

#### Caso B: $\bar{x} = 0 \land \bar{y} \neq 0$
Siamo sull'asse delle $y$, o meglio ci vogliamo avvicinare all'asse delle ordinate. Facciamo allora il limite del rapporto incrementale per entrambe le derivate parziali sapendo che $\bar{x} = 0$:
$$
\begin{align}

\partial_{x}f(0, \bar{y}) =& \lim_{h \to 0} \frac{f(0+h, \bar{y}) -f(0, \bar{y})}{h} = \lim_{h \to 0} \frac{\sqrt{|h|}\sqrt{|\bar{y}|} - \sqrt{0}\sqrt{|y|}}{h} \\
=& \lim_{h \to 0} \frac{\sqrt{|h|}\sqrt{|\bar{y}|}}{h} = \begin{cases} +\infty & h \to 0^{+} \\ -\infty & h \to 0^{-} \end{cases} \implies \nexists \partial_{x}f(0, \bar{y})

\end{align}
$$

Controlliamo, per completezza, l'esistenza di $\partial_{y}f(0, \bar{y})$:
$$
\begin{align}
\partial_{y}f(0, \bar{y}) =& \lim_{h \to 0} \frac{f(0, \bar{y}+h) - f(0, \bar{y})}{h} = \lim_{h \to 0} \frac{\sqrt{0}\sqrt{|\bar{y}+h|} - 0}{h} \\
=& \lim_{h \to 0} \frac{0}{h} = 0 \implies \exists \partial_{y}f(0, \bar{y})
\end{align}
$$

#### Caso C: $\bar{x} \neq 0 \land \bar{y} = 0$
Possiamo supporre, correttamente, che questo caso sia speculare al precedente: $\exists \partial_{x}f(\bar{x}, 0)$ e $\nexists \partial_{y}f(\bar{x}, 0)$.

#### Caso D: $\bar{x} = 0 \land \bar{y} = 0$
In questo caso ci avviciniamo verso l'origine.
$$
\begin{align}

\partial_{x}f(0, 0) =& \lim_{h \to 0} \frac{f(0+h, 0) - f(0, 0)}{h} = \lim_{h \to 0} \frac{\sqrt{|h|}\sqrt{0} - \sqrt{0}\sqrt{0}}{h} \\
=& \lim_{h \to 0} \frac{0}{h} = 0 \implies \exists \partial_{x}f(0, 0)

\end{align}
$$

E simmetricamente otteniamo
$$\partial_{y}f(0, 0) = 0 \implies \exists \partial_{y}f(0, 0)$$

### Differenziabilità
Sapendo che il 1° criterio per la differenziabilità è proprio l'esistenza di tutte le derivate parziali, _possiamo concentrarci solo sul caso A e sul caso D_.

Caso A: per un teorema (ancora non visto) scopriamo che tutte le funzioni elementari, per cui anche le loro composizioni, sono differenziabili --> non dobbiamo verificare nient'altro.

Caso D: dobbiamo ottenere lo sviluppo di Taylor al 1° ordine su $f$ nel punto $(\bar{x}, \bar{y}) = (0, 0)$, per cui devo verificare se
$$f(x, y) = f(0, 0) + \nabla f(0, 0) \cdot (x-0, y-0) + o(||(x-0, y-0)||)$$
e io so che $f(0, 0) = 0$, $\nabla f(0, 0) = (0, 0)$, perciò devo solo verificare
$$f(x, y) = o(||(x, y)||) \iff \sqrt{|x|}\sqrt{|y|} = o(||(x, y)||) = o(\sqrt{x^{2}+y^{2}})$$[^2]

ovvero, per la definizione di [[O-piccolo|o-piccolo]] che
$$\lim_{(x, y) \to (0, 0)} \frac{\sqrt{|x|}\sqrt{|y|}}{\sqrt{x^{2}+y^{2}}} = 0$$

un bellissimo limite in 2 variabili.
Usiamo un trucchetto che ci consente di verificare o meno questo limite usando le [[Successione numerica|successioni]]: il [[Limite formulato per successione|limite definito per successione]].

Per cui il limite vale $\iff$
$$\forall(x_{j}, y_{j})_{j \in \mathbb{N}} \neq (0, 0), \ \ (x_{j}, y_{j}) \stackrel{j \to +\infty}{\to} (0, 0) \ \ \implies \ \ \lim_{j \to +\infty} \frac{\sqrt{|x_{j}|}\sqrt{|y_{j}|}}{\sqrt{x_{j}^{2}+y_{j}^{2}}} = 0$$

Allora per "smentire" questo limite, usando le [[Proprietà dei connettivi e quantificatori|proprietà dei quantificatori]] mi posso _ridurre a dimostrare l'esistenza di una successione per cui il limite non vale_.

Scelgo allora $(x_{j}, y_{j}) = \left(\frac{1}{j}, \frac{1}{j}\right)$. Così facendo il limite viene
$$\lim_{j \to +\infty} \frac{\sqrt{|\frac{1}{j}|}\sqrt{|\frac{1}{j}|}}{\sqrt{\frac{1}{j}^{2} + \frac{1}{j}^{2}}} = \lim_{j \to +\infty} \frac{\frac{1}{j}}{\sqrt{2} \frac{1}{j}} = \frac{1}{\sqrt{2}} \neq 0$$

Per cui **$f$ non è differenziabile in $(0, 0)$, nonostante esistano le derivate parziali**!


## Proposizioni
### Continuità
Sappiamo che per una funzione $f: \mathbb{R}^{n} \to \mathbb{R}$, _l'esistenza delle derivate parziali non implica la continuità di $f$_. Ma, sostituendo alla condizione la differenziabilità otteniamo che l'implicazione è vera!

> Data $f: \mathbb{R}^{2} \to \mathbb{R}$ e fissato un punto $(\bar{x}, \bar{y}) \in \mathbb{R}^{2}$, allora
> $$f \text{ differenziabile in } (\bar{x}, \bar{y}) \implies f \text{ continua in } (\bar{x}, \bar{y})$$

#### Dimostrazione
Suppongo, per ipotesi, $f$ differenziabile in $(\bar{x}, \bar{y})$, perciò $\exists \partial_{x}f(\bar{x}, \bar{y})$, $\exists \partial_{y}f(\bar{x}, \bar{y})$ e $f(\bar{x}+h, \bar{y}+k) = f(\bar{x}, \bar{y}) + \partial_{x}f(\bar{x}, \bar{y}) \cdot (h) + \partial_{y}f(\bar{x}, \bar{y}) \cdot (k) + o(||(h, k)||)$ per $(h, k) \in \mathbb{R}^{2}, \ (h, k) \to (0, 0)$.

Devo dimostrare che $f$ è continua, ovvero che
$$\lim_{(h, k) \to (0, 0)} f(\bar{x} + h, \bar{y} + k) = f(\bar{x}, \bar{y})$$

Utilizzo allora la verifica del limite usando la sua formulazione per successione, per cui devo verificare che
$$\forall (h_{j}, k_{j})_{j \in \mathbb{N}} \neq (0, 0), \ (h_{j}, k_{j}) \to (0, 0) \ \ \implies \ \ \lim_{j \to +\infty} f(\bar{x} + h_{j}, \bar{y} + k_{j}) = f(\bar{x}, \bar{y})$$

So che $f(\bar{x} + h_{j}, \bar{y} + k_{j})$ per ipotesi e per la differenziabilità di $f$ è uguale a $f(\bar{x}, \bar{y}) + \partial_{x}f(\bar{x}, \bar{y}) \cdot (h) + \partial_{y}f(\bar{x}, \bar{y}) \cdot (k) + o(||(h, k)||)$, per cui sostituisco nel limite e ottengo da verificare che
$$\lim_{j \to +\infty} f(\bar{x}, \bar{y}) + \partial_{x}f(\bar{x}, \bar{y}) \cdot (h_{j}) + \partial_{y}f(\bar{x}, \bar{y}) \cdot (k_{j}) + o(||(h_{j}, k_{j})||) = f(\bar{x}, \bar{y})$$

Notiamo che, sapendo $\exists \partial_{x}f(\bar{x}, \bar{y})$ e $\exists \partial_{y}f(\bar{x}, \bar{y})$, per $j \to +\infty$ avremo $h_{j} \to 0$, $k_{j} \to 0$ e che $o(||(h_{j}, k_{j})||) \to 0$ (ovvio), per cui non rimane che
$$\lim_{j \to +\infty} f(\bar{x}, \bar{y}) = f(\bar{x}, \bar{y})$$

**Qed**.

### Condizioni sufficienti
Si può dimostrare che una _$f$ è differenziabile anche se esistono le derivate parziali e sono semplicemente continue in ogni punto_, senza dover verificare Taylor.

> Sia $f: \mathbb{R}^{2} \to \mathbb{R}$ tale che $\exists \partial_{x}f, \exists \partial_{y}f$ ed entrambe sono continue in ogni punto, allora
> $$\begin{align} & \forall (\bar{x}, \bar{y}) \in \mathbb{R}^{2}. \ \forall (h, k) \in \mathbb{R}^{2}, \ (h, k) \neq (0, 0). \ \exists \theta, \bar{\theta} \in ]0, 1[ : \\ & f(\bar{x}+h, \bar{y}) = f(\bar{x}, \bar{y}) + \partial_{x}f(\bar{x}+\theta h, \bar{y})h \ \ \ \land \ \ \ f(\bar{x}, \bar{y}+k) = f(\bar{x}, \bar{y}) + \partial_{y}f(\bar{x}, \bar{y}+\bar{\theta}k)k \end{align}$$
> o, semplicemente per certi parametri $\theta, \bar{\theta}$ vale lo sviluppo di Taylor al 1° ordine, per cui _$f$ è differenziabile_.

#### Dimostrazione
La dimostrazione richiede di usare il [[Teorema di Lagrange|teorema di Lagrange]] in $\mathbb{R}^{n}$.

Partiamo col dimostrare che $\exists \theta \in ]0, 1[ : f(\bar{x}+h, \bar{y}) = f(\bar{x}, \bar{y}) + \partial_{x}f(\bar{x}+\theta h, \bar{y})h$, che posso scrivere come
$$f(\bar{x}+h, \bar{y}) - f(\bar{x}, \bar{y}) = \partial_{x}f(\bar{x}+\theta h, \bar{y})h$$

Vogliamo usare Lagrange, per cui consideriamo una funzione ausiliaria $g(t) = f(\bar{x} + th, \bar{y})$. Notiamo che
$$g(0) = f(\bar{x}, \bar{y})$$
e
$$g(1) = f(\bar{x}+h, \bar{y})$$
per cui $$f(\bar{x}+h, \bar{y}) - f(\bar{x}+\bar{y}) = g(1) - g(0)$$

Ora, per Lagrange[^3] io so che
$$\exists \theta \in ]0, 1[ : g'(\theta) = \frac{g(1) - g(0)}{1-0}$$

Quindi prima calcolo la derivata $g'(t)$ usando il limite del rapporto incrementale
$$g'(t) = \lim_{s \to 0} \frac{g(t + s) - g(t)}{s} = \lim_{s \to 0} \frac{f(\bar{x} + th + sh, \bar{y}) - f(\bar{x}+th, \bar{y})}{s} = \lim_{s \to 0} \frac{f(\bar{x} + th + sh, \bar{y}) - f(\bar{x}+th, \bar{y})}{sh} \cdot h$$
cioè
$$g'(t) = \partial_{x}f(\bar{x}+th, \bar{y})h$$

ottengo, sostituendo alla proposizione precedente, che
$$\exists \theta \in ]0, 1[ : \partial_{x}f(\bar{x} + \theta h, \bar{y})h = f(\bar{x}+h, \bar{y}) - f(\bar{x}, \bar{y})$$

proprio ciò che volevamo dimostrare.

Per dimostrare $\exists \bar{\theta} \in ]0, 1[ : f(\bar{x}, \bar{y}+k) = f(\bar{x}, \bar{y}) + \partial_{y}f(\bar{x}, \bar{y}+\bar{\theta}k)k$ ripeto lo stesso procedimento per $\bar{y}$.

**Qed**.

## Referenze
[^1]: letteralmente Taylor in $n$ variabili
[^2]: per la definizione di [[Norma euclidea|norma]]
[^3]: nota che _posso applicare Lagrange perché $g$ è derivabile_, in quanto $g'$ (si veda dopo) è continua per ipotesi di $\partial_{x}f$ e $\partial_{y}f$ continue