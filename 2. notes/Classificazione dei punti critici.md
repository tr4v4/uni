---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 11-05-2024 18:34:19
links:
  - "[[Lecture 09052024141025]]"
---
# Classificazione dei punti critici
---
## Punti critici
> I punti critici di una [[Funzione a più variabili|funzione a più variabili]] si classificano in:
> 1. **massimo** (locale/globale);
> 2. **minimo** (locale/globale);
> 3. **sella**.

### Massimo
### Minimo
### Sella
> Sia $f: \mathbb{R}^{n} \to \mathbb{R}$ con $\partial_{jk}f$ continua $\forall j, k$, un punto critico $\bar{x}$ si dice di sella se
> $$\forall \delta > 0, \exists x^{-}, x^{+} \in I(\bar{x}, \delta) : f(x^{-}) < f(\bar{x}) < f(x^{+})$$

<u>Osservazione</u>: per $n = 1$ i _punti di sella corrispondono ai punto di flesso a tangente orizzontale_. Si veda $f(x) = x^{3}$ in $x = 0$.

## Classificazione
> Sia $f: \mathbb{R}^{n} \to \mathbb{R}$, assumo $\partial^{2}_{jk}f$ continue in $\mathbb{R}^{n}$ $\forall j, k \in \{1, \cdots, n\}$; sia $\bar{x} \in \mathbb{R}^{n}$ un punto critico, allora:
> 1. $Hf(\bar{x}) > 0 \implies \bar{x}$ minimo locale;
> 2. $Hf(\bar{x}) < 0 \implies \bar{x}$ massimo locale;
> 3. $Hf(\bar{x})$ indefinito $\implies \bar{x}$ sella.

### Dimostrazione
#### 1.
Sappiamo che $\nabla f(\bar{x}) = 0 \land Hf(\bar{x}) > 0$. E devo dimostrare
$$\exists \delta > 0 : f(\bar{x} + h) - f(\bar{x}) \geq 0 \ \ \forall h \in \mathbb{R}^{n}, |h| < \delta$$

Usiamo Taylor al 2° ordine, ossia
$$f(\bar{x} + h) - f(\bar{x}) = <\nabla f(\bar{x}), h> + \frac{1}{2}<Hf(\bar{x})h, h> + o(|h|^{2})$$

e, sapendo $\nabla f(\bar{x}) = 0$ otteniamo
$$f(\bar{x} + h) - f(\bar{x}) = \frac{1}{2}<Hf(\bar{x})h, h> + o(|h|^{2})$$

Ora usiamo [[Forma quadratica#1|questo lemma]] che ci dice che se $Hf(\bar{x}) > 0$ allora $\exists \lambda > 0 : <Hf(\bar{x})h, h> \geq \lambda |h|^{2} \ \ \forall h \in \mathbb{R}^{n}$. Perciò abbiamo che
$$f(\bar{x} + h) - f(\bar{x}) = \frac{1}{2}<Hf(\bar{x})h, h> + o(|h|^{2}) \geq \frac{1}{2} \lambda |h|^{2} + o(|h|^{2}) = \frac{|h|^{2}}{2}\left(\lambda + \frac{o(|h|^{2})}{|h|^{2}}\right)$$

Scelgo allora $\delta > 0$ tale che
$$|\frac{o(|h|^{2})}{|h|^{2}}| < \frac{\lambda}{2} \ \ \forall h \in \mathbb{R}^{n}, h \neq 0, |h| < \delta$$
così, se $|h| < \delta$ vale
$$f(\bar{x} + h) - f(\bar{x}) = \frac{1}{2}<Hf(\bar{x})h, h> + o(|h|^{2}) \geq \frac{1}{2} \lambda |h|^{2} + o(|h|^{2}) = \frac{|h|^{2}}{2}\left(\lambda + \frac{o(|h|^{2})}{|h|^{2}}\right) \geq \frac{|h|^{2}}{2}\left(\lambda - \frac{\lambda}{2}\right) > 0$$

**Qed**.

#### 2.
Analoga a 1.

#### 3.
Devo dimostrare
$$\forall \delta > 0, \exists x^{-}, x^{+} \in I(\bar{x}, \delta) : f(x^{-}) < f(\bar{x}) < f(x^{+})$$

Dimostriamo che è sempre possibile trovare un $x^{+}$ tale che $f(\bar{x}) < f(x^{+})$; il caso per $x^{-}$ è analogo. Quindi scegliamo di dimostrare
$$\exists v^{+} \in \mathbb{R}^{n}, v^{+} \neq \underline{0} \ : \ \ f(\bar{x} + tv^{+}) - f(\bar{x}) > 0 \ \ \ \ \forall t \to 0$$

Usiamo sempre Taylor al 2° ordine, ovvero
$$f(\bar{x} + tv^{+}) - f(\bar{x}) = <\nabla f(\bar{x}), tv^{+}> + \frac{1}{2}<Hf(\bar{x})tv^{+}, tv^{+}> + o(|tv^{+}|^{2})$$

per cui dalle ipotesi, e dalle proprietà del prodotto scalare possiamo scrivere come
$$f(\bar{x} + tv^{+}) - f(\bar{x}) = \frac{t^{2}}{2} <Hf(\bar{x})v^{+}, v^{+}> + o(t^{2})$$

Sapendo che $<Hf(\bar{x})v^{+}, v^{+}> > 0$ la dimostrazione si conclude immediatamente, infatti
$$f(\bar{x} + tv^{+}) - f(\bar{x}) = \frac{t^{2}}{2}\left(<Hf(\bar{x})v^{+}, v^{+}> + \frac{o(t^{2})}{t^{2}}\right) > 0 \ \ \ \ \forall t \to 0$$

## Referenze