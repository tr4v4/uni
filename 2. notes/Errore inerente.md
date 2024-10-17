---
tags:
  - category/note
  - status/finished
  - topic/calcolo-numerico
date: 04-10-2024 15:18:43
links:
  - "[[Lecture 30092024131914]]"
---
# Errore inerente
---
## Introduzione
> L'**errore inerente** è definito su di un calcolo numerico come l'[[Errore di troncamento|errore di troncamento]] senza considerare l'[[Errore algoritmico|errore algoritmico]], e quindi sull'_errore causato dalla rappresentazione dei dati ma non sulla sua propagazione causata dall'[[Aritmetica floating-point|aritmetica floating-point]]_.

Si suppone allora che ci sia solo un errore nella rappresentazione dei dati, ma che le operazioni tra questi siano fatte in aritmetica reale. A questo punto _la distanza tra il risultato finale del calcolo e il risultato effettivo sarà solamente causata all'errore di rappresentazione dei dati in input_: questo è l'_errore inerente_.

## Conseguenze
L'errore inerente è un indice fondamentale che dovrebbe essere tenuto in conto nell'applicazione di [[Algoritmo|algoritmi]] su problemi di calcolo numerico.

### Risoluzione di sistemi lineari
Si scopre infatti che negli [[Algoritmi per la risoluzione di sistemi lineari|algoritmi per la risoluzione di sistemi lineari]] l'**errore inerente pone un vincolo non indifferente**.

Consideriamo la seguente immagine
![[Drawing 2024-09-30 14.46.11.excalidraw|750]]

dove:
- $(A, b)$ è il problema posto in input;
- $x$ è la soluzione perfetta ottenuta dal metodo risolutivo $t$;
- $t$ è la funzione che mappa il problema alla sua soluzione ottenuta con operazioni aritmetiche reali (di fatto $A^{-1}b$);
- $\Delta$ è la differenza causata dall'errore di rappresentazione;

L'errore inerente in questo caso è allora
$$\|x + \Delta x - x\| = \|\Delta x\|$$

Si desidera mettere in relazione l'errore inerente $\|\Delta x\|$ con l'errore di rappresentazione dei dati in input $\|\Delta A\| + \|\Delta b\|$.

Quello che si scopre è che:
$$\frac{\|\Delta x\|}{\|x\|} \leq k(A)\left( \frac{\|\Delta A\|}{\|A\|} + \frac{\|\Delta b\|}{\|b\|} \right)$$

dove:
- $\frac{\|\Delta x\|}{\|x\|}$ è l'errore relativo inerente, detto **relative error**;
- $\frac{\|\Delta A\|}{\|A\|} + \frac{\|\Delta b\|}{\|b\|}$ è l'errore relativo sui dati, detto **relative backward error**;
- $k(A)$ è il [[Numero di condizione|numero di condizione]] della matrice $A$.

#### Risultato
Questo ci insegna un qualcosa di importante: l'**errore inerente non dipende solo dall'errore di rappresentazione sui dati in input, né dall'algoritmo; bensì dalla matrice $A$ stessa**.

E non ci si può fare nulla! _Anche modificando la codifica dei dati per ottenere un errore di arrotondamento più basso, se $k(A)$ è gigantesco, anche l'errore sui dati in output lo sarà_!

Formalmente diciamo allora che: se $k(A) \gg 1$ allora la matrice $A$ si dice **mal condizionata**, e il sistema $Ax = b$ si dice **mal posto**.

<u>Nota bene</u>: "mal posto" è un aggettivo del problema, ossia del sistema, e non dell'algoritmo.

Un altro risultato estremamente importante è il seguente: l'**errore algoritmico influisce pochissimo sull'errore dei dati in output**! Ossia _la propagazione dell'errore di rappresentazione sui dati in input è minima rispetto all'errore inerente_.

## Referenze
- esempio del [calcolo dell'errore inerente sulle matrici di Hilbert](https://virtuale.unibo.it/pluginfile.php/2334725/mod_resource/content/0/26.%20Simultaneous%20Linear%20Equations%2C%20Part%205_%20Error%20bounds%20for%20linear%20algebra%2C%20condition%20numbers%2C%20matrix%20norms%2C%20etc.%20%E2%80%94%20MATH%20375.%20Elementary%20Numerical%20Analysis%20%28with%20Python%29.pdf)