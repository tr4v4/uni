---
tags:
  - category/note
  - status/finished
  - topic/calcolo-numerico
date: 30-10-2024 14:10:36
links:
  - "[[Lecture 15102024091721]]"
  - "[[Lecture 04112024131513]]"
---
# Regolarizzazione alla Tikhonov
---
## Introduzione
> La **regolarizzazione alla Tikhonov** è una tecnica di [[Regolarizzazione|regolarizzazione]] dell'[[Approssimazione ai minimi quadrati|approssimazione ai minimi quadrati]] della forma:
> $$\min_{\alpha} \frac{1}{2} {\|X\alpha  - y\|_{2}}^{2} + \frac{\lambda}{2} {\|\alpha\|_{2}}^{2}$$
> in cui l'iperparametro $\lambda$ è chiamato **termine di regolarizzazione alla Tikhonov** e _regola la forza con cui il modello deve minimizzare il vettore dei coefficienti $\alpha$ rispetto alla risoluzione dei minimi quadrati_.

## Risoluzione
Porre il [[Gradiente|gradiente]] di quella formula a 0 produce un risultato simile alle _equazioni normali standard_:
$$X^{T}X\alpha - X^{T}y + \lambda \alpha = 0$$
che poi diventa
$$(X^{T}X + \lambda I) \alpha = X^{T}y$$

Si tratta quindi di una _versione estesa dei minimi quadrati_, che porta però a risultati ottimi.

## Problemi inversi
Nell'ambito dei [[Problemi inversi|problemi inversi]] lineari è possibile regolarizzare la sommatoria della soluzione usando questa stessa tecnica. In particolare se considero $f_{i}$ i fattori di filtro tali che la soluzione $x^{*}$ del problema regolarizzato
$$\min_{x} {\|Ax - y^{\delta}\|_{2}}^{2} + \lambda {\|Lx\|_{2}}^{2}$$
viene calcolata come
$$x^{*} = \sum\limits_{i=1}^{n} f_{i} \frac{u_{i}^{T}y^{\delta}}{\sigma_{i}} v_{i}$$
allora questi sono della forma:
$$f_{i} = \frac{\sigma_{i}^{2}}{\sigma_{i}^{2} + \lambda}$$

La scelta del parametro di Tikhonov è indipendente dalle [[Condizioni discrete di Picard|condizioni di Picard]], per cui bisogna andare per tentativi.

## Referenze