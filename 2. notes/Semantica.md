---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 06-11-2023 19:14:57
links:
  - "[[Lecture 31102023161330]]"
  - "[[Lecture 02112023091408]]"
  - "[[Lecture 08112023131119]]"
---
# Semantica
---
## Introduzione
> La **semantica** è la parte della linguistica che studia il _significato delle parole_, degli _insiemi di parole_, delle _frasi_ e dei _testi_.
> Nel contesto della logica la **semantica è una [[Funzione matematica|funzione]] che associa a ogni [[Connotazione|connotazione]] una [[Denotazione|denotazione]] in un [[Dominio di interpretazione|dominio di interpretazione]] fissato**.

Si considerino:
- [[Connotazione]] --> parte di una frase corretta sintatticamente
- [[Denotazione]] --> significato attribuito a una connotazione
- [[Dominio di interpretazione]] --> [[Insieme|insieme]] dei possibili significati
- [[Sintassi]] --> insieme di tutte le connotazioni

In poche parole, se scomponiamo una frase in un insieme $A$ di _connotazioni_, corrette sintatticamente, e abbiamo un insieme $B$ _dominio di interpretazione_, la funzione _semantica_ associa ogni elemento di $A$ alla sua [[Immagine di funzione|immagine]] _denotazione_ in $B$ ([[Definizione di essere sottoinsieme|sottoinsieme]] del dominio di interpretazione)[^1][^2].

### Rapporto con sintassi
> La sintassi è l'insieme delle regole del regno della connotazione; un esempio di sintassi usata in logica è la [[Logica proposizionale|logica proposizionale]].
> La semantica è l'insieme delle regole del regno della denotazione; un esempio di semantica usata in logica è la [[Semantica classica|semantica classica]], da cui deriva la [[Logica classica|logica classica]].

## Conseguenze
Punti di vista differenti sul mondo, non per forza giusti o sbagliati, portano alla costruzione di differenti semantiche, quindi a _diversi significati associati a stesse connotazioni_.

Dalle semantiche si formano le logiche su cui sono basate le matematiche: **il ruolo della semantica è fondamentale**. 

## Tipologie
- [[Semantica intesa]], detta anche _naturale_ o _principale_
- [[Semantica classica]]

## Referenze
[^1]: la semantica non è [[Funzione suriettiva|suriettiva]]! Non potrebbe associare infatti tutti i significati denotativi a una connotazione
[^2]: è lo stesso rapporto _dicotomico_ che si presenta tra **bit** e **significato dei bit**, per cui _[[RAM#Definizione|è il programma a dare un significato ai dati]]_