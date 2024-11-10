---
tags:
  - category/note
  - status/finished
  - topic/calcolo-numerico
date: 10-11-2024 20:27:32
links:
  - "[[Lecture 04112024131513]]"
---
# Principio di massima discrepanza
---
## Introduzione
> Il **principio di massima discrepanza** è la tecnica di [[Regolarizzazione|regolarizzazione]] più usata nei [[Problemi inversi|problemi inversi]] lineari risolti ai [[Problema dei minimi quadrati|minimi quadrati]].

## Idea
Se si suppone di avere delle informazioni sul rumore $\delta$, e in particolare il valore della sua [[Norma euclidea|norma]] 2
$$\|\delta\|_{2}$$
, allora si può scegliere il parametro $\lambda$ di [[Regolarizzazione alla Tikhonov|Tikhonov]] tale che sia soddisfatta la seguente relazione:
$${\|Ax_{\text{tik}} - y^{\delta}\|_{2}}^{2} = \nu {\|\delta\|_{2}}^{2}$$

In altre parole, **se il residuo ${\|Ax_{\text{tik}} - y^{\delta}\|_{2}}^{2}$ è uguale alla norma del rumore al quadrato per $\nu$ (un valore di tolleranza, solitamente $1.01$ o $1.001$), allora quel $\lambda$ è ottimale**.

## Referenze