---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 27-08-2025 23:30:39
links:
  - "[[Lecture 12112024110924]]"
---
# Linguaggio LL(k)
---
## Introduzione
> Un [[Linguaggio formale|linguaggio]] $L$ e' di classe $LL(k)$ se esiste una [[Grammatiche|grammatica]] $G$ di [[Grammatiche LL(k)|classe]] $LL(k)$ tale che $L = L(G)$.

## Teoremi
### Gerarchia
> $\forall k \geq 0$, la classe dei linguaggi $LL(k+1)$ contiene strettamente la classe dei linguaggi $LL(k)$.

![[gerarchia-linguaggi-llk.png]]

<u>Nota bene</u>: le grammatiche $LL(0)$ sono "stupide". Si tratta di grammatiche in grado di generare al massimo una sola parola: $L(G) = \{w\}$.

Quindi fondamentalmente la grande maggioranza di grammatiche sono $LL(1)$. E, **se $G$ non e' $LL(1)$ spesso la si puo' manipolare** (attraverso [[Fattorizzazione a sinistra|fattorizzazione a sinistra]], eliminazione della [[Ricorsione sinistra|ricorsione sinistra]], [[Grammatica ambigua|disambiguazione]], ecc...[^1]) **trasformandola in una [[Grammatiche equivalenti|equivalente]] $LL(1)$**.

#### Esempio
La grammatica
$$S \to aSb|ab|c$$
e' $LL(2)$ e non $LL(1)$. Ma attraverso una semplice fattorizzazione diventa
$$S \to aT|c \ \ \ \ \ T \to Sb|b$$
che e' $LL(1)$!
Di conseguenza il linguaggio generato da entrambe le grammatiche
$$L = \{a^{n}b^{n} | n \geq 1\} \cup \{a^{n}cb^{n} | n \geq 0\}$$
e' di classe $LL(1)$, perche' $G'$ (la grammatica fattorizzata) lo e'!

## Referenze

[^1]: in generale [[Semplificazione delle grammatiche|semplificazione della grammatica]]
