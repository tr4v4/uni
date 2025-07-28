---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 12-07-2025 14:25:34
links:
  - "[[Lecture 28042025111320]]"
---
# CDMA
---
## Introduzione
> Il **Code Division Multiple Access (CDMA)** è una tecnologia di accesso multiplo wireless implementata insieme al [[DSSS]].

## Funzionamento
Ad ogni host viene assegnato un codice univoco (chip sequence!) per codificare i bit che inviera'. Poi, sia i bit che i codici trasformano lo `0` in `-1` e lo `1` in `+1`.
Quindi, si moltiplica ogni bit per il codice, e si trasmette il risultato. Il ricevitore sara' in grado di scindere i segnali in base ai codici dei mittenti!

Per esempio, $A$ vuole inviare `1` e ha codice `010011`; $B$ vuole inviare `0` e ha codice `110101`. Quindi (a seguito della trasformazione e della moltiplicazione) $A$ inviera' `-1 1 -1 -1 1 1`, mentre $B$ inviera' `-1 -1 1 -1 1 -1`.
Ora, i due segnali si sommano (somma vettoriale): $C$ ricevera' `-2 0 0 -2 2 0`.
Se $C$ volesse ricevere il segnale inviato solo da $A$, gli basterebbe fare il [[Prodotto scalare|prodotto scalare]] tra il segnale e il codice di $A$:
$$(-2, 0, 0, -2, 2, 0) \cdot (0, 1, 0, 0, 1, 1) = 6$$
In questo caso, $6 > 0$, per cui $A$ ha inviato `1`. Nel caso di $B$, invece, il risultato sarebbe stato $-6 < 0$, quindi $B$ ha inviato `0`.

![[cdma-1.png]]

![[cdma-2.png]]

## Referenze