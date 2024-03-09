---
tags:
  - category/note
  - status/finished
  - topic/architettura-degli-elaboratori
date: 08-10-2023 19:38:49
links:
  - "[[Lecture 05102023130513]]"
  - "[[Lecture 09102023132029]]"
---
# Conversione binario-decimale
---
## Introduzione
Per passare dal [[Codice binario|codice binario]] a quello decimale bisogna fare qualche sforzo in più rispetto alla [[Conversione binario-ottale-esadecimale|conversione tra binario, ottale ed esadecimale]], perché 10 non è una potenza di 2.

## Binario $\to$ decimale
Ci sono 2 strade che si possono intraprendere:
- attraverso la [[Codifica numeri interi#Introduzione|sommatoria]]
- attraverso la _tecnica delle moltiplicazioni successive_
  ![[tecnica-delle-moltiplicazioni-successive.png]]
## Decimale $\to$ binario
In questo caso invece si usa la _tecnica delle divisioni successive_ (derivata dalle moltiplicazioni successive):
![[tecnica-delle-divisioni-successive.png]]

### Numero con la virgola
<u>Attenzione</u>: esiste un algoritmo a parte, che si basa sullo stesso principio delle divisioni successive, per **calcolare i numeri binari da decimali con la virgola**.

![[conversione-float-binario.png]]

Seguendo lo schema sopra riportato, notiamo come le cifre binarie dopo la virgola seguono la stessa regola della [[Codifica numeri interi#Introduzione|sommatoria]] della codifica dei numeri interi. Da $2^{0}$ si va indietro con $2^{-1}$, quindi $2^{-2}$ e così via, per tutti i numeri dopo la virgola.

Per questo si usa questo algoritmo per calcolare per un qualunque numero con la virgola la sua corrispondenza binaria:
1. si moltiplica il numero con la virgola per 2
2. il numero intero risultato (che sia 0 o 1) è la i-esima cifra del numero binario
3. tolgo l'intero dal risultato e ripeto dallo step 2 fino a che il numero con la virgola non diventa 0

<u>Cosa importantissima</u> da notare è che alcuni numeri decimali _finiti_ **in binario non lo sono**! Ci sono numeri come `0.3` che in _binario sono periodici_.

## Referenze
- spiegazione [numeri negativi con la virgola](https://youtu.be/QMAsLeBDUQw)