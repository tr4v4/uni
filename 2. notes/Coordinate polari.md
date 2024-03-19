---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 18-03-2024 20:45:55
links:
  - "[[Lecture 11032024131300]]"
---
# Coordinate polari
---
## Introduzione
> Le **coordinate polari** sono un sistema di rappresentazione di [[Vettore|vettori]] dello [[Spazio euclideo|spazio euclideo]] $\mathbb{R}^{2}$ che si ricava dall'operazione di [[Normalizzazione|normalizzazione]] dei vettori. In particolare un vettore $v = (x, y) \in \mathbb{R}^{2}$ può essere rappresentato nel seguente modo
> $$(x, y) = r \cdot (\cos(\theta), \sin(\theta))$$
> dove:
> - $r  = ||(x, y)|| > 0$ è detto _modulo_ (ed è la [[Norma euclidea|norma]] di $(x, y)$);
> - $\theta \in [0, 2 \pi[$ è detto _argomento_;
> 
> Si dice che $r$ e $\theta$ sono _coordinate polari_ di $v$.

## Prodotto scalare
Posso scrivere il [[Prodotto scalare|prodotto scalare]] in coordinate polari. Considero $(x, y) = (r\cos{\theta}, r\sin{\theta})$ e $(u, v) = (\mu \cos{\phi}, \mu \sin{\phi})$. Allora ho che
$$(x, y) \cdot (u, v) = r \mu \cos{\theta}\cos{\phi} + r \mu \sin{\theta}\sin{\phi} = r \mu (\cos{\theta}\cos{\phi} + \sin{\theta}\sin{\phi}) = r \mu \cos(\phi - \theta) = |(x, y)| \cdot |(u, v)| \cdot \cos(\phi - \theta)$$

per cui in definitiva
$$(x, y) \cdot (u, v) = |(x, y)| \cdot |(u, v)| \cdot \cos(\phi - \theta)$$
dove $\cos{\phi - \theta}$ è l'angolo tra i vettori $(x, y)$ e $(u, v)$.

## Referenze