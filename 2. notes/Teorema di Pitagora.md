---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 27-09-2023 10:00:42
links:
  - "[[Lecture 25092023093433]]"
---
# Teorema di Pitagora
---
## Definizione
> In un triangolo rettangolo, **la somma dei quadrati dei due cateti è uguale al quadrato dell'ipotenusa**.
> $${c_{1}}^{2} + {c_{2}}^{2} = i^{2}$$

## Dimostrazione
Ci sono due modi per dimostrare questo teorema, _per decomposizione_ e _per similitudine_.

### Per decomposizione
![[Drawing 2023-09-27 10.15.19.excalidraw|750]]

Consideriamo l'area del _quadrato risultante_
$$Area(ABCD) = (a+b)^{2}$$
dove $a+b$ è il lato.
Ora, dimostrando che il quadrilatero centrale sia un quadrato con la regola della _somma degli angoli interni di un triangolo che fa sempre 180°_ (derivata dal [[V postulato di Euclide]]), possiamo affermare che la stessa area $ABCD$ può essere scritta anche come la somma delle 4 aree dei triangoli rettangoli con la somma del quadrato centrale cui lati sono le ipotenusa:
$$Area(ABCD) = 4\left(\frac{ab}{2}\right)+ c^{2} = 2ab + c^{2}$$
Uguagliando le due aree otteniamo
$$(a+b)^{2} = 2ab + c^{2}$$
con cui si giungerà alla fine a
$$c^{2} = a^{2} + b^{2}$$
**dimostrando il teorema di pitagora**.

### Per similitudine
![[Drawing 2023-09-27 10.37.56.excalidraw|750]]

Notiamo che i triangoli $T1$ e $T2$ sono **simili**, perché hanno gli stessi angoli. E a sua volta $T$ è simile a $T1$ e $T2$, che anch'esso con gli stessi angoli. Sappiamo allora che per questa loro proprietà _il rapporto delle aree dei triangoli è uguale al rapporto che coesiste tra le loro ipotenuse_. Possiamo quindi affermare
$$\frac{A(T1)}{A(T)} = \left(\frac{a}{c}\right)^{2}$$
e
$$\frac{A(T2)}{A(T)} = \left(\frac{b}{c}\right)^{2}$$
Ora, sapendo che la somma delle aree di $T1$ e $T2$ compone l'area di $T$
$$A(T1) + A(T2) = A(T)$$
dividendo tutto per $A(T)$ otteniamo
$$\frac{A(T1)}{A(T)} + \frac{A(T2)}{A(T)} = 1$$
da cui, sostituendo i rapporti tra le aree con i rapporti tra le ipotenuse
$$\left(\frac{a}{c}\right)^{2} + \left(\frac{b}{c}\right)^{2} = 1$$
e quindi
$$a^{2} + b^{2} = c^{2}$$
**dimostrando il teorema di Pitagora**.

## Referenze