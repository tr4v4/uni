---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 13-10-2023 10:46:15
links:
  - "[[Lecture 02102023093041]]"
---
# Limite finito di successione
---
## Definizione
> Presa una successione $(a_{n})_{n}$ e un valore $L \in \mathbb{R}$, si dice
> $$\lim_{n \to +\infty} a_{n} = L$$
> se
> $$\forall \epsilon > 0, \exists \delta = \delta(\epsilon) \in \mathbb{R}_{+} : \forall n > \delta : | a_{n} - L | < \epsilon$$
> Il che significa: **per qualunque valore epsilon positivo esiste un valore delta di soglia oltre il quale la successione produce una differenza con il limite inferiore a epsilon**.

Visualizzando meglio l'ultima parte della definizione, trasformando il [[Valore assoluto|valore assoluto]] avremmo
$$L - \epsilon < a_{n} < L + \epsilon$$
per cui
![[definizione-limite-finito-convergente.png]]

Vale a dire che per **qualunque** valore di $\epsilon$ deve esistere una soglia $\delta$ oltre la quale la successione cade nell'**intorno** $L - \epsilon < a_{n} < L + \epsilon$.

La potenzialità di questa definizione sta nel $\forall \epsilon$, che ci consente di rimpicciolire sempre di più l'intervallo in cui deve cadere $a_{n}$, portando per valori infinitesimali proprio ad $L$.

Si scrive infatti anche
$$a_{n} \longrightarrow_{n \to +\infty} L$$

e soprattutto si dice che $a_{n}$ è **convergente**.

### Esempio
Proviamo con questa definizione che $a_{n} = \frac{n-1}{n}$ tende a 1:
$$\lim_{n \to +\infty} \frac{n-1}{n}= 1$$
Quindi applichiamo la definizione di limite
$$|\frac{n-1}{n} - 1| < \epsilon$$
ottenendo
$$|\frac{-1}{n}| = \frac{1}{n} < \epsilon$$
Ora applichiamo i reciproci ($n > 0$)
$$n > \frac{1}{\epsilon}$$
Ed ecco fatto: abbiamo ottenuto la soglia
$$\delta = \frac{1}{\epsilon}$$
oltre il quale è verificato
$$|\frac{n-1}{n} - 1| < \epsilon$$
_Provare per credere_.

## Referenze