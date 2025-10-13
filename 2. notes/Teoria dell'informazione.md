---
tags:
  - category/note
  - status/finished
  - topic/introduzione-all-apprendimento-automatico
date: 01-10-2025 19:38:20
links:
  - "[[Lecture 26092025131224]]"
---
# Teoria dell'informazione
---
## Introduzione
>La **teoria dell'informazione** di Shannon comprende concetti quali:
> - [[Entropia|entropia]];
> - [[Guadagno informativo|guadagno informativo]].

## Interpretazione
### Entropia
Il legame tra entropia e informazione si ottiene dal seguente ragionamento. L'informazione, in particolare, viene associata alla [[Probabilita'|probabilita']] di ogni dato, vale a dire la "sorpresa" associata all'evento:
- un evento con probabilita' 1 non trasmette alcuna informazione --> $I(1) = 0$;
- dati due [[Eventi indipendenti|eventi indipendenti]] con probabilita' $p_{1}, p_{2}$, sappiamo che la probabilita' congiunta e' $p_{1} \cdot p_{2}$, ma l'informazione acquisita e' la somma delle informazioni dei due eventi indipendenti --> $I(p_{1} \cdot p_{2}) = I(p_{1}) + I(p_{2})$;
- ci aspettiamo, inoltre, che l'informazione sia antimonotona rispetto alla probabilita' --> se un evento ha una probabilita' alta, e avviene, ottengo poca informazione; e viceversa.

Da queste 3 regole, possiamo dedurre la formula per l'informazione:
$$I(p) = -\log(p)$$
Questa, guarda caso, e' proprio la _funzione di informazione_ che compone la sommatoria dell'entropia!

Di conseguenza, Shannon dice che l'**entropia misura il numero medio di bits richiesti per trasmettere il valore prodotto da una sorgente stocastica $X$**.

Se per esempio abbiamo $n$ eventi tutti con la stessa probabilita', allora serviranno $\log{n}$ bits per codificare ogni possibile risultato. Questo _si lega molto bene con la [[Codifica di Huffman|codifica di Huffman]]_: se assumiamo che ogni testo abbiamo una [[Distribuzione uniforme discreta|distribuzione uniforme]] di lettere dell'alfabeto, allora l'entropia e' massima, dobbiamo usare sempre $\log{n}$ bits per codificare ogni carattere; ma se cosi' non e' (e nella realta' non lo e') allora possiamo assegnare meno bit a certi caratteri.

## Referenze