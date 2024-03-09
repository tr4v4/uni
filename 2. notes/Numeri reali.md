---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 27-09-2023 09:38:45
links:
  - "[[Lecture 25092023093433]]"
  - "[[Lecture 29092023135952]]"
---
# Numeri reali
---
## Introduzione
Immaginiamo di porre su una retta tutti i [[Numeri razionali|numeri razionali]]. Possiamo dire che tutti i punti della retta sono associati a un numero razionale? O meglio, esiste una [[Biiettività di una funzione|funzione biunivoca]] tra $\mathbb{Q}$ e i punti della retta?

Fino a un certo punto, nella storia, si è sempre creduto che i **numeri razionali contenessero ogni possibile numero**, e che in certo senso allora la **realtà fosse misurabile e rappresentabile con delle frazioni**. Ma con il [[Teorema di Pitagora|teorema di Pitagora]] _le cose cambiarono_.

Prendendo infatti un triangolo rettangolo con cateti uguali a 1, l'ipotenusa è $\sqrt{2}$, **un numero che deve esistere**. Allora esso appartiene ai razionali? $\sqrt{2} \in \mathbb{Q}$? Ebbene, è [[Dimostrazione radice di 2 non razionale|dimostrabile]] che no, $\sqrt{2} \notin \mathbb{Q}$.

E' anzi [[Dimostrazione radice di un numero primo non razionale|possibile dimostrare]] che $\sqrt{p} \notin \mathbb{Q}$ per ogni $p$ (_numero primo_), e, [[Teorema dell'infinità dei numeri primi|sapendo che i numeri primi sono infiniti]] si arriva facilmente alla conclusione che **esiste un'infinità di numeri non appartenenti ai razionali**. _E questo è un problema..._

Un grosso problema. Si dimostra infatti a sua volta che **ci sono successioni di numeri razionali che convergono a numeri non razionali**. Sembra assurdo, ma è la verità.

E' per questo che nasce la necessità di creare $\mathbb{R}$, l'**insieme dei numeri reali**.

## Scopo
> L'**insieme dei numeri reali** $\mathbb{R}$ nasce come insieme in grado di _esaudire_ la _retta dei razionali_, _completandone i vuoti non razionali_: $\mathbb{R} = \mathbb{Q} + \text{vuoti}$.

Si dice allora che $\mathbb{R}$ è un **insieme continuo**, ovvero avente quella proprietà che manca a $\mathbb{Q}$. Ma come si dimostra questa proprietà?
Esistono due approcci:
- per _costruzione esplicita_
- per _assiomi_
	- alla fine ci basta dimostrare che $\mathbb{R}$ contenga i _periodici e non_
	- [[Proprietà di completezza di R]]

## Conseguenze
[[Dimostrazione R non numerabile|Dimostrando]] $|\mathbb{N}| < |\mathbb{R}|$ si conclude che $\mathbb{R}$ ha la **cardinalità del continuo**.

## Referenze
- [[Maggiorante]]
- [[Minorante]]
- [[Massimo]]
- [[Minimo]]
- [[Estremo superiore]]
- [[Estremo inferiore]]