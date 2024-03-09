---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 13-10-2023 11:41:26
links:
  - "[[Lecture 09102023094657]]"
---
# Funzioni trigonometriche
---
## Introduzione
Le principali funzioni trigonometriche sono:
- **seno**
- **coseno**
- **tangente**

### Seno e coseno
Presa la [[Circonferenza goniometrica|circonferenza goniometrica]] e fissato un angolo al centro $\alpha$ che individua un punto $P$ su di essa, si definisce **seno** la **coordinata $y$ di $P$** e **coseno** la **coordinata $x$ di $P$**.
![[seno-coseno.webp]]

#### Caratteristiche
Seno e coseno sono _funzioni periodiche_, infatti:
- $\sin(\alpha \pm 2\pi) = \sin(\alpha)$
- $\cos(\alpha \pm 2\pi) = \cos(\alpha)$

Essendo periodiche su il periodo di 1 giro, per ogni giro, si dice che sono periodiche in $2k \pi$ (dove $k \in \mathbb{N}^{*}$).

Il seno è una funzione [[Disparità di una funzione|dispari]], mentre il coseno è [[Parità di una funzione|pari]].

#### Grafici
```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [-10,10,-10,10]
disableZoom: false
grid: true
---
f(x) = sin(x)
g(x) = cos(x)
```
- in blu il _seno_
- in rosso il _coseno_

### Tangente
Per uno stesso angolo $\alpha$ e per una retta parallela alle ordinate e passante per $(1, 0)$ che si interseca con la retta dell'angolo in un punto $P$, si definisce **tangente** la **coordinata $y$ di $P$**.
![[tangente.png]]

#### Caratteristiche
La tangente non è definita per gli angoli $\frac{\pi}{2}, \frac{3}{2}\pi$. Si ricava la tangente anche con
$$\tan(\alpha) = \frac{\sin(\alpha)}{\cos(\alpha)}$$
(_per cui tra l'altro si conferma il dominio della tangente..._)

La tangente è anch'essa una _funzione periodica_ ma non in $2k \pi$ (come per seno e coseno), bensì solo per $k \pi$.

#### Grafico
```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [-10,10,-10,10]
disableZoom: false
grid: true
---
f(x) = tan(x)
```


## Legge fondamentale
$$\sin^{2}\alpha + \cos^{2}\alpha = 1$$
Questa legge lega il seno al coseno, per cui è possibile da uno ricavare l'altro, _ponendo la giusta attenzione all'angolo per capirne il segno_.

## Referenze