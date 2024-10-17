---
tags:
  - category/note
  - status/finished
  - topic/calcolo-numerico
date: 04-10-2024 14:41:39
links:
  - "[[Lecture 30092024131914]]"
---
# Fattorizzazione di Cholesky
---
## Introduzione
> La **fattorizzazione di Cholesky** è un metodo per la [[Algoritmi per la risoluzione di sistemi lineari|risoluzione di sistemi lineari]] che si identifica come caso particolare della [[Fattorizzazione LU|fattorizzazione LU]]. Nella fattispecie, se $A$ è una [[Matrice|matrice]] [[Matrice simmetrica|simmetrica]] [[Forma quadratica#Segno|definita positiva]], allora la fattorizzazione può essere fatta come
> $$A = L \cdot L^{T}$$

L'algoritmo, quindi, funziona allo stesso modo della fattorizzazione LU, ma sapendo che $U = L^{T}$, per trovare $L$ basta fare $L = (L^{T})^{T}$.

## Algoritmo
L'algoritmo rimane lo stesso della fattorizzazione LU, ma al posto di richiamare dalla libreria _scipy_ `sp.linalg.lu(A)` si usa `sp.linalg.cholesky(A)`.

## Complessità
La [[Complessità computazionale|complessità computazionale]] risulta essere:
$$O\left(\frac{n^{3}}{6}\right)$$

## Referenze