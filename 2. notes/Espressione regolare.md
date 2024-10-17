---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 07-10-2024 21:51:36
links:
  - "[[Lecture 03102024120247]]"
---
# Espressione regolare
---
## Introduzione
> Fissato un alfabeto $A = \{a_{1}, \cdots, a_{n}\}$, definiamo le **espressioni regolari** su $A$ in notazione [[Backus-Naur Form|BNF]] come
> $$r ::= \varnothing|\epsilon|a|r \cdot r|r / r| r^{*}$$
> ossia, un'espressione regolare $r$ può essere:
> - $\varnothing$, _nulla_[^1];
> - $\epsilon$, _una stringa vuota_;
> - $a$, _una lettera dell'alfabeto_;
> - $r \cdot r$, _una concatenazione tra due sottoespressioni regolari $r$_;
> - $r/r$, _una scelta tra due sottoespressioni regolari $r$_;
> - $r^{*}$, _una ripetizione di una sottoespressione regolare $r$_.

<u>Nota bene</u>: si tratta di una [[Sintassi astratta|sintassi astratta]], quindi piena di ambiguità, ma facilmente disambiguabile con le parentesi. Inoltre, per semplicità si ha che:
- _la concatenazione, la disgiunzione e la ripetizione associano a sx_;
- _la precedenza degli operatori segue la formula $* > \cdot > /$_;

## Operatori ausiliari
Si possono anche aggiungere ulteriori "produzioni" ad $r$, come:
- _ripetizione positiva_: $r^{+}$, ossia non dà la possibilità di essere $\epsilon$ (si può ottenere anche da $rr^{*}$ o $r^{*}r$)
- _possibilità_: $r?$ ossia $r|\epsilon$ (per esempio $a^{*} \cdot b|a^{*}$ si può riassumere in $a^{*}\cdot b?$)
- _elenco_: $[a_{1}, \cdots, a_{n}]$, che sta per $a_{1}|\cdots|a_{n}$, se gli elementi sono ordinati si può scrivere come $[a_{1}-a_{n}]$

## Definizione regolare
E' possibile talvolta dare una lista di definizioni per descrivere in modo più intuitivo un'espressione regolare. Fondamentalmente si associa ad ogni produzione di $r$ un nuovo simbolo che sarà descritto in seguito, come di seguito:
- $d_{1} := r_{1}$
- $d_{2} := r_{2}$
- $\cdots$
- $d_{k} := r_{k}$

Si prenda come esempio l'espressione regolare che rappresenta i numeri decimali con segno:
$$\text{num\_con\_segno}:=\text{segno} \cdot \text{cifre} (. \text{cifre})?$$
dove:
- $\text{segno} := -|+$
- $\text{cifre} := \text{cifra}^{+}$
- $\text{cifra} := [0-9]$

## Equivalenze
> Due espressioni regolari $r$ e $s$ si dicono **equivalenti** $\iff$
> $$\mathscr{L}[r] = \mathscr{L}[s]$$
> e si denota con
> $$r \simeq s$$

### Proprietà
- $r|s \simeq s|r$
- $r|(s|t) \simeq(r|s)|t$
- $r|r \simeq r$
- $r \cdot (s \cdot t) \simeq (r \cdot s) \cdot t$
- $\epsilon \cdot r \simeq r \simeq r \cdot \epsilon$
- $(r^{*})^{*} \simeq r^{*}$
- $r(s|t) \simeq rs|rt$
- $(r|s)t \simeq rt|st$
- $\varnothing^{*} \simeq \epsilon$
- $r|\varnothing \simeq r$
- $r \cdot \varnothing \simeq \varnothing \simeq \varnothing \cdot r$
- $(\epsilon | r)^{*} \simeq r^{*}$
- $(r^{*}s^{*})^{*} \simeq (r|s)^{*}$

## Esempi
L'espressione regolare per rappresentare numeri decimali senza segno è:
$$[0-9]^{+}(\epsilon|.[0-9]^{+})$$

## Referenze
- [[Linguaggio denotato da un'espressione regolare]]

[^1]: l'[[Assioma dell'insieme vuoto|insieme vuoto]]