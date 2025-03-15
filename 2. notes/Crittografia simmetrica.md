---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 09-03-2025 12:10:33
links:
  - "[[Lecture 18022025152022]]"
---
# Crittografia simmetrica
---
## Introduzione
> La **crittografia simmetrica** comprende una serie di algoritmi per la [[Crittografia|crittografia]] che utilizzano _una sola chiave per cifrare e decifrare_.

![[chiave-simmetrica.png]]

## Algoritmi
I piu' importanti algoritmi a chave simmetrica (o privata) sono:
- [[Cifrario di Cesare]]
	- la chiave è una permutazione dell'alfabeto, quindi $26!$ chiavi possibili
	- essendo a chiave simmetrica rimane il problema della condivisione della chiave
	- inoltre fare un'analisi delle frequenze è semplicissimo
- [[Cifrario a rotazione]]
	- è un Cesare ma in cui si scelgono $n$ permutazioni, e ciclicamente ad ogni $n$ lettere si cambia permutazione
- [[DES]]
	- usato nella modernità
	- si usa una chiave a 56 bit, simmetrica, che viene applicata su blocchi di 64 bit di plaintext
	- si può decifrare in un giorno!
	- con 3DES si cifra 3 volte con 3 chiavi diverse
- [[AES]]
	- molto piu' sicuro del DES

## Problema
Il chiaro **problema di questo approcco e' la condivisione della chiave**! Se esiste un meccanismo sicuro per scambiare la chiave simmetrica, allora possiamo usare direttamente quello per scambiare i messaggi!

## Referenze
- [[Crittografia asimmetrica]]