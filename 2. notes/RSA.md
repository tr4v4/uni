---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 09-03-2025 12:33:15
links:
  - "[[Lecture 18022025152022]]"
---
# RSA
---
## Introduzione
> L'**RSA** e' un algoritmo per la [[Crittografia asimmetrica|crittografia asimmetrica]] che _sfrutta le proprieta' dei [[Numeri primi|numeri primi]] e dell'[[Aritmetica modulare|aritmetica modulare]] per generare chiavi pubbliche e private sicure_ (tale che la funzione di cifratura sia [[Funzione one-way|one-way]]).

## Funzionamento
I passi per generare una chiave pubblica $K^{+}$ e una privata $K^{-}$ tale che
$$\forall m. \ \ \ K^{-}(K^{+}(m)) = m$$
sono i seguenti:
1. scegli due primi grandi $p, q$ (1024 bits);
2. $n = pq, z = (p-1)(q-1)$;
3. scegli $e < n$ che non ha fattori comuni con $z$, quindi dev'essere coprimo con $z$;
4. scegli $d : ed - 1$ sia esattamente divisibile per $z$, ossia $ed \mod z = 1$;
5. la chiave pubblica è $(n, e)$, quella privata è $(n, d)$.

### Cifratura
A questo punto, dato un messaggio $m (< n)$ che interpreto come un intero (posso sempre farlo) ho che
$$c = m^{e} \mod n$$

### Decifratura
Viceversa, dato un messaggio cifrato $c$, ho che
$$m = c^{d} \mod n$$

## Formula generale
La magia sta nella formula, dimostrabile usando le leggi dell'aritmetica modulare
$$m = (m^{e} \mod n)^{d} \mod n$$

Da questo formula, inoltre, si ricava una proprieta' che si rivelera' fondamentale: **l'ordine di cifratura delle chiavi e' indifferente**. Nel senso che posso cifrare con la pubblica e poi decifrare con la privata, ma anche fare anche il contrario.
$$K^{-}(K^{+}(m)) = m = K^{+}(K^{-}(m))$$

Il procedimento opposto non e' affatto inutile: si tratta della [[Firma digitale|firma]], il meccanismo principale usato per l'[[Autenticazione|autenticazione]]. Di fatto, **possiamo unire i due utilizzi della formula, per poter garantire confidenzialita' e autenticazione usando sempre l'RSA**.

Brevemente, se $A$ vuole inviare a $B$, garantendo confidenzialita' e autenticazione, inviera'
$$K_{B}^{+}(K_{A}^{-}(m))$$
ossia il messaggio cifrato prima con la sua chiave privata (autenticazione), e poi con la chiave pubblica di $B$ (segretezza).

Quindi, $B$, per decifrare il messaggio e verificare l'autenticazione di $A$, fara'
$$K_{A}^{+}(K_{B}^{-}(m))$$

## Utilizzi
L'algoritmo sopra descritto, e' estremamente inefficiente e costoso. Di solito, infatti, **l'RSA si utilizza soltanto per scambiare le chiavi di sessione**, ovvero [[Crittografia simmetrica|chiavi simmetriche]] che, una volta scambiate in modo sicuro, saranno usate per cifrare tutta la comunicazione usando algoritmi a chiave privata (piu' efficienti dell'RSA).

## Referenze