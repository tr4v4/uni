---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 15-10-2023 22:14:28
links:
  - "[[Lecture 12102023091734]]"
---
# Deduzione naturale
---
## Introduzione
Si tratta dello **studio delle dimostrazioni**, ovvero del concepimento di _prove_. In particolare ci si occupa di _formalizzare delle frasi logiche_ per dimostrarne la validità.

<u>Attenzione</u>: **i linguaggi naturali sono ambigui**[^1], per cui si utilizza un formalismo standard per la dicitura delle stesse.

In questo caso, infatti, per dimostrare deduzioni naturali si utilizzano gli [[Albero di deduzione naturale|alberi di deduzione naturale]].

### Esempio
La frase
> "_Se_ oggi piove _allora_ prendo l'ombrello, _se_ prendo l'ombrello _allora_ non mi bagno. Quindi _se_ oggi piove _allora_ non mi bagno"

può essere formalizzata in
$$(P \implies O) \land (O \implies \neg B) \implies P \implies \neg B$$
dove:
- $P$ è la proposizione "_oggi piove_"
- $O$ è la proposizione "_prendo l'ombrello_"
- $B$ è la proposizione "_mi bagno_"

## Referenze
- [[Notazioni]]

[^1]: stesso motivo per cui è fondamentale rappresentare gli [[Algoritmo|algoritmi]] con metodologie standard/universali, come i [[Diagrammi di flusso|diagrammi di flusso]]