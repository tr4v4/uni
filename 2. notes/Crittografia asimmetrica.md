---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 09-03-2025 12:23:55
links:
  - "[[Lecture 18022025152022]]"
---
# Crittografia asimmetrica
---
## Introduzione
> La **crittografia asimmetrica** comprende una serie di algoritmi per la [[Crittografia|crittografia]] che utilizzano _due chiavi, una pubblica e una privata, per poter cifrare e decifrare_.

In modo particolare, ogni interlocutore ha:
- una **chiave pubblica**, conosciuta da tutti;
- una **chiave privata**, conosciuta solo dall'interlocutore stesso.

## Principio di funzionamento
Il principio di funzionamento e' il seguente: se $A$ vuole bandare un messaggio $m$ a $B$, allora cifra $m$ con la chiave pubblica $K_{B}^{+}$ di $B$ (dopo avergliela chiesta); $B$ quando riceve il messaggio lo decifra usando la sua chiave privata $K_{B}^{-}$.
![[crittografia-asimmetrica.png]]

Di per se', tutti gli algoritmi a crittografia asimmetrica funzionano in questo modo. Differiscono pero' nella creazione delle chiavi pubbliche e private tale che valga
$$m = K_{B}^{-}(K_{B}^{+}(m))$$

In modo particolare si vuole garantire che la conoscenza della chiave pubblica non permetta di fare brute-force sulla chiave privata per decifrare il messaggio: in altre parole la funzione di cifratura dev'essere [[Funzione one-way|one-way]].

## Algoritmi
I principali algoritmi a chiave asimmetrica sono:
- [[Diffie-Hellman]];
- [[RSA]].

## Problemi
Una delle debolezze di questi algoritmi e' che **per messaggi molto brevi diventa estremamente facile la loro decifratura**: conoscendo la dimensione del messaggio $m$, si puo' infatti vedere per ogni combinazione possibile di lettere di quella dimensione se corrisponde al messaggio cifrato con la chiave pubblica.

## Referenze