---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 26-04-2024 16:47:34
links:
  - "[[Lecture 08042024130916]]"
  - "[[Lecture 24042024142113]]"
---
# Derivata direzionale
---
## Introduzione
> Sia $f: \mathbb{R}^{2} \to \mathbb{R}$ una [[Funzione a più variabili|funzione a 2 variabili]], $(\bar{x}, \bar{y}) \in \mathbb{R}^{2}$ un punto e $v = (v_{1}, v_{2})$ un [[Vettore|vettore]] [[Normalizzazione|normalizzato]] (t.c. $||v|| = 1$, ovvero la sua [[Norma euclidea|norma]] è uguale a 1), allora si dice che $f$ è derivabile nella direzione $v$ nel punto $(\bar{x}, \bar{y})$ se
> $$\exists\frac{\partial_{f}}{\partial_{v}} (\bar{x}, \bar{y}) = \lim_{t \to 0} \frac{f((\bar{x}, \bar{y}) + t(v_{1}, v_{2})) - f(\bar{x}, \bar{y})}{t} \in \mathbb{R}$$

Fondamentalmente si tratta di una generalizzazione del concetto di [[Derivata parziale|derivata parziale]], che considera oltre ai vettori $e_{1}, e_{2}$ della [[Base canonica|base canonica]] tutti i possibili altri vettori di $\mathbb{R}^{2}$.

Di fatto se scelgo $v = (1, 0)$ ottengo $\partial_{v}f(\bar{x}, \bar{y}) = \partial_{x}f(\bar{x}, \bar{y})$; viceversa per $v = (0, 1)$ ho $\partial_{v}f(\bar{x}, \bar{y}) = \partial_{y}f(\bar{x}, \bar{y})$.

### In $\mathbb{R}^{n}$
Chiaramente le derivate direzionali esistono anche per $n > 2$, e si definiscono nel seguente modo:
> Sia $f: \mathbb{R}^{n} \to \mathbb{R}$, $\bar{x} \in \mathbb{R}^{n}$ e $v \in \mathbb{R}^{n}$ t.c. $||v|| = 1$, allora
> $$\frac{\partial_{f}}{\partial_{v}}(\bar{x}) = \lim_{t \to 0} \frac{f(\bar{x}+tv) - f(\bar{x})}{t}$$

## Direzione di massima crescita
Un problema che ci si pone nello studio di funzioni a più variabili è quello di **trovare, in un determinato punto, tra tutte le derivate direzionali quella che ha valore massimo**.

Si sta cercando in particolare:
$$v_{\max} \in \mathbb{R}^{n} : ||v_{\max}|| = 1 : \frac{\partial f}{\partial v_{\max}}(x) = \max \{\frac{\partial f}{\partial v}(x) | v \in \mathbb{R}^{n}, ||v|| = 1\}$$

### Proposizione
Il problema si risolve dimostrando la seguente proposizione:
> Data $f: \mathbb{R}^{n} \to \mathbb{R}$ [[Funzione differenziabile|differenziabile]] in $\bar{x} \in \mathbb{R}^{n}$ con $\nabla f(\bar{x}) \neq \underline{0}$, allora si ha che
> 1. $v_{\max} = \frac{\nabla f(\bar{x})}{||\nabla f(\bar{x})||}$
> 2. $\frac{\partial f}{\partial v_{\max}} (x) = ||\nabla f(x)||$
> 
> ovvero che _il vettore di massima crescita è il gradiente normalizzato, e la derivata direzionale rispetto a tal vettore è la norma del gradiente_.

#### Dimostrazione
Diamo una dimostrazione in $\mathbb{R}^{2}$ usando le [[Coordinate polari|coordinate polari]]. Per dimostrarlo in $\mathbb{R}^{n}$ è necessario basarsi sulla [[Disuguaglianza di Cauchy-Schwarz|disuguaglianza di Cauchy-Schwarz]].

##### 1.
Voglio cercare un $v = (v_{1}, v_{2})$ tale che $v = v_{\max}$. Scrivo il gradiente in coordinate polari, ovvero
$$\nabla f(x, y) = (r\cos{\theta}, r\sin{\theta})$$
con $r = ||\nabla f(x, y)||$ e $\theta \in [0, 2\pi]$.
A questo punto per trovare un generico $(v_{1}, v_{2})$ che scrivo sempre in coordinate polari come $(\cos{\phi}, \sin{\phi})$[^1] che _massimizzi la crescita_ utilizzo la [[Teorema del gradiente|formula del gradiente]] e calcolo $\partial_{v}$:
$$\partial_{v}f = (r\cos{\theta}, r\sin{\theta}) \cdot (\cos{\phi}, \sin{\phi}) = r\cos{\theta}\cos{\phi} + r\sin{\theta}\sin{\phi} = r\cos(\phi - \theta)$$

Perciò sto trovando quel vettore dipendente da $\phi$ che massimizzi $\partial_{v}f$, ovvero $r\cos{\phi-\theta}$. Scegliendo di fatto _$\phi = \theta$ viene $\cos{0} = 1$, ovvero un massimale della derivata direzionale $\partial_{v}f$_, per cui
$$v_{\max} = (\cos{\theta}, \sin{\theta})$$
dove $\nabla f(x, y) = (r\cos{\theta}, r\sin{\theta})$.
E' facile notare come **$v_{\max}$ sia il gradiente di $f$ normalizzato** (a cui è stato tolto il modulo $r$)!

##### 2.
Una volta dimostrato $v_{max} = (\cos{\theta}, \sin{\theta})$, per dimostrare $\frac{\partial f}{\partial v_{\max}} (x, y) = ||\nabla f(x, y)||$ è sufficiente considerare la formula del gradiente e avere che
$$\frac{\partial f}{\partial v_{\max}} (x, y) = \nabla f(x, y) \cdot (v_{1}, v_{2}) = (r\cos{\theta}, r\sin{\theta}) \cdot (\cos{\theta}, \sin{\theta}) = r\cos^{2}{\theta} + r\sin^{2}{\theta} = r(\cos^{2}{\theta}+\sin^{2}{\theta}) = r$$
dove $r$ è proprio il modulo del gradiente, ovvero $||\nabla f(x, y)||$.

## Referenze
- [[Teorema del gradiente]]

[^1]: nota che non ha nessun modulo perché devo avere $v_{\max}$ unitario