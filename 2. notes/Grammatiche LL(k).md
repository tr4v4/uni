---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 27-08-2025 22:49:52
links:
  - "[[Lecture 12112024110924]]"
---
# Grammatiche LL(k)
---
## Introduzione
> Una [[Grammatiche|grammatica]] e' $LL(K)$ $\iff$ ogni casella della [[Tabella di parsing LL(k)|tabella di parsing]] $LL(k)$ contiene al piu' una produzione.

## Teoremi
### Teoremone
> Raccogliamo dei risultati fondamentali riguardanti le grammatiche $LL(k)$:
> 1. _una grammatica [[Ricorsione sinistra|ricorsiva sinistra]] non è $LL(k)$ per nessun $k$_ (si consideri $S \to Sa|b$);
> 2. _una grammatica [[Grammatica ambigua|ambigua]] non è $LL(k)$ per nessun $k$_;
> 3. _se $G$ è $LL(k)$ per qualche $k$, allora $G$ non è ambigua_;
> 4. _se $G$ è $LL(k)$, allora $L(G)$ è [[Linguaggio libero deterministico|libero deterministico]]_;
> 5. _esiste $L$ libero deterministico tale che non esiste $G$ di classe $LL(k)$ (per nessun $k$) tale che $L = L(G)$_.

Il punto fondamentale e' sicuramente l'ultimo: ci dice che **la classe dei linguaggi coperti da $LL(k)$ è più piccola di quella dei liberi deterministici**. Per questa ragione e' necessario introdurre i [[Parser bottom-up|parser bottom-up]].

#### Esempio
Il linguaggio
$$L = \{a^{i}b^{j} | i \geq j\}$$
e' libero deterministico. Infatti il [[DPDA]] che lo [[Linguaggio accettato|accetta]] per stato finale e'
![[dpda-lib-det-non-llk.png]]

Una possibile [[Grammatiche libere|grammatica libera]] $G$ per $L$ e':
$$S \to aS | B \ \ \ \ \ B \to \epsilon | aBb$$

Ora, intuitivamente, come faccio da $S$ a scegliere tra $aS$ e $B$? _Dovrei leggere fino in fondo l'input per sapere quante $b$ in meno di $a$ ci sono nella stringa_! Si puo' infatti dimostrare che **$G$ non puo' essere $LL(k)$ per nessun $k$**, infatti per quanto grande sia $k$ posso sempre trovare una stringa piu' lunga che richiede di leggere piu' di $k$ simboli di [[Look-ahead|look-ahead]].

Addirittura, e' dimostrabile che per questo particolare linguaggio non esiste una $G'$ e un $k$ tale che $L(G') = L$ e $G' \in LL(k)$. Infatti in questo caso e' proprio il [[Linguaggio LL(k)|linguaggio a non essere]] $LL(k)$!

## Referenze