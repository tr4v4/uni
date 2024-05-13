---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 14-10-2023 17:43:21
links:
  - "[[Lecture 09102023094657]]"
---
# Funzioni trigonometriche inverse
---
## Introduzione
Le principali [[Funzioni trigonometriche|funzioni trigonometriche]] _inverse_ sono:
- **arcoseno**
- **arcocoseno**
- **arcotangente**

### Arcoseno e arcocoseno
Il seno da $\mathbb{R}$ a $\mathbb{R}$ non è [[Funzione inversa|invertibile]]: è infatti una funzione né [[Funzione iniettiva|iniettiva]] né [[Funzione suriettiva|suriettiva]]. Per poter renderla invertibile devo restringere sia il dominio che il codominio:
- per renderla suriettiva --> restringo il codominio = $[-1, 1]$
- per renderla iniettiva --> restringo il dominio (facendo attenzione a non perdere la suriettività) = $[-\frac{\pi}{2}, \frac{\pi}{2}]$

Ottengo ora un seno invertibile. Per cui inverto la legge di associazione, il dominio con il codiminio e ottengo l'**arcoseno**:
$$f: [-1, 1] \to \left[-\frac{\pi}{2}, \frac{\pi}{2}\right]$$
![[arcsin.png]]
<u>Attenzione</u>: come conseguenza del fatto che l'inversione di funzione ci è costato in dominio e codominio, $\arcsin(\sin(x)) = x$ solo quando $x \in [-\frac{\pi}{2}, \frac{\pi}{2}]$.

Il coseno da $\mathbb{R}$ a $\mathbb{R}$ non è [[Funzione inversa|invertibile]]: è infatti una funzione né [[Funzione iniettiva|iniettiva]] né [[Funzione suriettiva|suriettiva]]. Per poter renderla invertibile devo restringere sia il dominio che il codominio:
- per renderla suriettiva --> restringo il codominio = $[-1, 1]$
- per renderla iniettiva --> restringo il dominio (facendo attenzione a non perdere la suriettività) = $[0, \pi]$

Ottengo ora un coseno invertibile. Per cui inverto la legge di associazione, il dominio con il codiminio e ottengo l'**arcocoseno**:
$$f: [-1, 1] \to [0, \pi]$$
![[arccos.png]]
<u>Attenzione</u>: come conseguenza del fatto che l'inversione di funzione ci è costato in dominio e codominio, $\arccos(\cos(x)) = x$ solo quando $x \in [0, \pi]$.

### Arcotangente
Anche la funzione tangente non è invertibile da $\mathbb{R}$ a $\mathbb{R}$, per questo si restringe in modo simile al seno:
- per renderla suriettiva --> restringo il codominio = $[-1, 1]$
- per renderla iniettiva --> restringo il dominio (facendo attenzione a non perdere la suriettività) = $]-\frac{\pi}{2}, \frac{\pi}{2}[$ (_a differenza del seno gli intervalli sono aperti, perché $\tan$ non è definita per quei valori_)

Ottengo ora una tangente invertibile. Per cui inverto la legge di associazione, il dominio con il codiminio e ottengo l'**arcotangente**:
$$f: [-1, 1] \to ]-\frac{\pi}{2}, \frac{\pi}{2}[$$
![[arctan.png]]
<u>Attenzione</u>: come conseguenza del fatto che l'inversione di funzione ci è costato in dominio e codominio, $\arctan(\tan(x)) = x$ solo quando $x \in ]-\frac{\pi}{2}, \frac{\pi}{2}[$.

## Referenze