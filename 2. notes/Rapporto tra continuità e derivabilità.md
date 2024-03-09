---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 27-10-2023 20:01:08
links:
  - "[[Lecture 27102023135003]]"
---
# Rapporto tra continuità e derivabilità
---
## Introduzione
C'è uno stretto legame tra la derivabilità e la continuità di una funzione, che in breve si sintetizza con la legge:
$$f \text{ derivabile} \implies f \text{ continua}$$

<u>Attenzione</u>: _non vale il contrario_. Se una funzione è continua non per forza è derivabile.

### Esempio
Prendiamo in esame $f = |x|$. Sappiamo dimostrare, usando i limiti destri e sinistri, che **per l'origine il [[Valore assoluto|valore assoluto]] è continuo**. Essendo continuo in tutti i punti del dominio, _possiamo creare la funzione derivata_.

Ci chiediamo quindi se
$$f'(x) = \begin{cases} 1 & \text{se } x \geq 0 \\ -1 & \text{se } x < 0 \end{cases}$$

Risulta chiaro come le derivate di destra e di sinistra non coincidano.

<u>Nota bene</u>: solo $|x|$ si è visto non essere derivabile, ma _non per forza dov'è presente un valore assoluto si esclude la derivabilità_ (es. $f = x|x|$).

## Dimostrazione
Per dimostrare che se $f$ è derivabile allora è per forza continua ci concentriamo sulla dimostrazione della continuità:
$$\lim_{x \to x_{0}} f(x) = f(x_{0})$$
che possiamo scrivere come
$$\lim_{x \to x_{0}} f(x) - f(x_{0}) = 0$$

Moltiplicando e dividendo per $x - x_{0}$ otteniamo
$$\lim_{x \to x_{0}} \frac{f(x) - f(x_{0})}{x - x_{0}} \cdot (x - x_{0}) = 0$$

Il limite del primo termine è $f'(x)$, poiché dalle ipotesi sappiamo che è derivabile; il limite invece del secondo termine è 0. Per cui abbiamo dimostrato che la tesi è sempre vera.

**Cvd**.

## Conseguenze
Questa legge non solo esprime il rapporto tra derivabilità e continuità, ma mette in evidenza che **la derivabilità è sintomo di una maggiore regolarità di una semplice funzione continua**. Vale a dire che una funzione derivabile è più vincolata, fa parte infatti di un [[Definizione di essere sottoinsieme|sottoinsieme]] stretto delle funzioni continue:
![[rapporto-continuità-derivabilità.png]]


## Referenze