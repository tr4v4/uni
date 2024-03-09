---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 06-11-2023 21:07:03
links:
  - "[[Lecture 31102023161330]]"
  - "[[Lecture 02112023091408]]"
---
# Logica classica
---
## Introduzione
> La **logica classica** ([[Logica proposizionale|proposizionale]]) si prefissa di _studiare la verità_ a partire da una serie di _assunzioni filosofiche sul mondo_, dando, secondo i principi della [[Semantica classica|semantica classica]], una _[[Denotazione|denotazione]] di verità o falsità alle [[Connotazione|connotazioni]]_.

## Assunzioni
Le assunzioni filosofiche su cui si basa la logica classica sono nascono dalla _visione platonica del mondo_:
1. ogni enunciato è vero o falso
2. **principio di non contraddizione** --> _un enunciato non può essere vero e falso allo stesso tempo_[^1]
3. **principio di non staticità** --> _il valore di verità non muta_
4. **principio di determinatezza** --> _il valore di verità di un enunciato è sempre determinato_

### Osservazioni
Si possono fare una serie di osservazioni sulle assunzioni della logica classica:
- il principio di non staticità _elimina il libero arbitrio e non dà spazio a una visione non-deterministica del mondo_
- il principio di determinatezza, unito a quello di staticità, prevede che _ogni cosa sia determinata, e che quindi potremmo essere onniscienti_ --> potenzialmente, conoscendo lo stato attuale del mondo, potremmo prevederne con certezza la sua evoluzione e tutto il futuro dell'universo
- la staticità è la determinatezza segnano il solco tra verità (classica) e conoscenza (non statica ma monotona, forse indeterminata)
- la staticità segna il solco tra verità e risorse

In conclusione si scopre che fondamentalmente la **logica classica è un'estrema semplificazione del mondo**.

## Interpretazione
Il [[Dominio di interpretazione|dominio di interpretazione]] _classico_ è
$$\{0, 1\}$$
dove:
- $0$ è il _falso_
- $1$ è il _vero_

Si deriva dai primi due punti delle assunzioni della logica classica. La rappresentazione con i [[Numeri naturali|numeri naturali]] risulta estremamente versatile per la rappresentazione aritmetica[^2] delle funzioni semantiche, e anche per scalare ad altre logiche cui dominio è l'intervallo [[Numeri reali|reale]] $[0, 1]$.

Una **funzione di interpretazione classica** o [[Mondo|mondo]] è una [[Funzione matematica|funzione]] che ha:
- dominio = l'_insieme delle variabili_ della [[Logica proposizionale|logica proposizionale]] $\{A, B, ...\}$
- codominio = il _dominio di interpretazione_ $\{0, 1\}$.

Tali interpretazioni, o _funzioni semantiche_, verranno indicate con $v$.

### Esempio
Se si ha:
- $v(A) = 0$ --> nel mondo $v$, $A$ è _falso_
- $v'(A) = 1$ --> nel mondo $v'$, $A$ è _vero_

Quindi: la **funzione semantica prenderà in ingresso le variabili $A, B, ...$ e il mondo $v$, e restituirà $0$ o $1$.

## Referenze
- [[Semantica classica]]

[^1]: avviene il contrario nelle [[Logica paraconsistente|logiche paraconsistenti]]
[^2]: meta-matematica!