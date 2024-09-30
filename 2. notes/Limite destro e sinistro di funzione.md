---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 19-10-2023 21:10:22
links:
  - "[[Lecture 16102023093744]]"
---
# Limite destro e sinistro di funzione
---
## Introduzione
Nell'ambito dei [[Limite al finito di funzione|limiti al finito di funzioni]] esistono i **limiti destri e sinistri**. Per uno stesso punto $x_{0}$, infatti, è possibile avvicinarsi sia da destra che da sinistra: spesso e volentieri questo _ci è utile nel momento in cui non siamo in grado di determinare con certezza il valore del limite per $x_{0}$_ (senza segno)[^1].

## Osservazione
E' importante precisare che i limiti destri e sinistri possono determinare o meno l'esistenza di un [[Limite al finito di funzione|limite al finito]].

> Se $L \in \mathbb{R} \cup \{+\infty\} \cup \{-\infty\}$
> allora
> $$\lim_{x \to x_{0}} f(x) = L \iff \begin{cases} \exists \lim_{x \to x_{0}^{-}} f(x), \lim_{x \to x_{0}^{+}} f(x) \\ \lim_{x \to x_{0}^{-}} f(x) = \lim_{x \to x_{0}^{+}} f(x) \\ \lim_{x \to x_{0}^{-}} f(x) = L = \lim_{x \to x_{0}^{+}} f(x) \end{cases}$$

Ciò significa che in caso contrario, ovvero qualora i limiti destro e sinistro per $x_{0}$ fossero discordanti, allora il limite per $x_{0}$ non esisterebbe!

## Casi speciali
Il limite destro e sinistro ritorna particolarmente utile nel momento in cui si vuole determinare il segno di un $\infty$ come risultato della [[Forme indeterminate|forma indeterminata]] $\frac{1}{0}$.

> Per risolvere $\lim_{x \to x_{0}} \frac{1}{f(x)}$ dove $f(x)$ si annulla in $x_{0}$, allora **si fanno entrambi i limiti destro e sinistro di $f(x)$** per determinare per ognuno di esso il segno:
> - _limite destro_
> 	- $0^{+}$ se $f(x) > 0$
> 	- $0^{-}$ se $f(x) < 0$
> - _limite sinistro_
> 	- $0^{+}$ se $f(x) > 0$
> 	- $0^{-}$ se $f(x) < 0$
> Se per entrambi i limiti viene lo stesso segno di $0$, e di conseguenza lo stesso segno di $\infty$, allora il limite esiste (per l'[[Limite destro e sinistro di funzione#Osservazione|osservazione precedente]]).

## Referenze
[^1]: attenzione, questo discorso vale sia per i limiti finiti che per quelli infiniti