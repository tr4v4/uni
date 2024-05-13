---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 05-05-2024 11:57:44
links:
  - "[[Lecture 03052024102451]]"
  - "[[Lecture 09052024141025]]"
---
# Studio del gradiente
---
## Introduzione
Se per [[Funzione matematica|funzioni]] a 1 variabile ($f: \mathbb{R} \to \mathbb{R}$) lo [[Studio di funzione|studio di funzione]] prevede lo [[Studio della derivata prima|studio della derivata prima]] per identificare i [[Massimo e minimo relativo|punti di massimo e di minimo relativi]], per [[Funzione a più variabili|funzioni a più variabili]] le cose cambiano.

Per $n = 1$, infatti, si hanno due approcci per identificare massimi e minimi di una funzione:
1. [[Studio del segno|studio del segno]] della [[Derivata|derivata]], ovvero risoluzione della disequazione $f'(x) \geq 0$;
2. condizioni differenziali di ordine superiore, ovvero risoluzione del sistema $\begin{cases} f'(x) = 0 \\ f''(x) > 0 \end{cases}$ --> $x$ è di minimo.

<u>Nota bene</u>: solitamente si utilizza il 1° metodo, perché più comodo e veloce, ma i due sono equivalenti.

Per $n \geq 2$, invece, _il 1° metodo è impraticabile_, perché _non possiamo studiare il [[Gradiente|gradiente]] $\nabla f(x) \geq 0$_. Perciò si deve seguire la strada della differenziabilità, cercando di generalizzare in $\mathbb{R}^{n}$ rispettivamente:
- condizioni del 1° ordine --> $f'(x) = 0$
- condizioni del 2° ordine --> $f''(x) > 0$

## Studio
### Condizioni del 1° ordine
Sappiamo che la scrittura $f'(x) = 0$ in $\mathbb{R}^{n}$ può essere tradotta come
$$\nabla f(x) = \underline{0}$$
dove $\underline{0}$ è il [[Vettore|vettore]] nullo di ordine $n$.

Inoltre è con il [[Teorema di Fermat|teorema di Fermat]] che si dimostra che $f'(\bar{x}) = 0 \implies \bar{x}$ punto di minimo o massimo relativo: dobbiamo ottenere lo stesso risultato con la condizione $\nabla f(\bar{x}) = \underline{0}$. Per fortuna si dimostra che ciò vale, con [[Teorema di Fermat#In $ mathbb{R} {n}$|Fermat in Rn]].

Si ha che:
> Data $f: \mathbb{R}^{n} \to \mathbb{R}$ [[Funzione differenziabile|differenziabile]] in $\bar{x} \in \mathbb{R}^{n}$, se $\nabla f(\bar{x}) = \underline{0}$ allora $\bar{x}$ si chiama **punto critico o stazionario**.

### Condizioni del 2° ordine
Per poter analizzare il 2° ordine del gradiente è necessario conoscere:
- [[Derivata parziale seconda|derivate parziali seconde]];
- [[Matrice hessiana|matrice hessiana]];
- [[Sviluppo in serie di Taylor#Resto di Lagrange|formula di Taylor in ordine 2 con resto di Lagrange]];
- [[Forma quadratica|forma quadratica]] e [[Forma quadratica hessiana|forma quadratica hessiana]].

In poche parole il processo logico è il seguente:
1. dalle derivate parziali costruiamo la matrice hessiana;
2. notiamo che la matrice hessiana, per il [[Teorema di Schwarz|teorema di Schwarz]], è una forma quadratica;
3. con la formula di Taylor in ordine 2 con resto di Lagrange dimostriamo che lo studio della forma quadratica hessiana ci consente di classificare i punti critici.

Una volta appreso il ragionamento si può studiare la [[Classificazione dei punti critici|classificazione dei punti critici]].

## Referenze