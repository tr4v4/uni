---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
  - topic/linguaggi-di-programmazione
date: 06-11-2023 19:14:57
links:
  - "[[Lecture 31102023161330]]"
  - "[[Lecture 02112023091408]]"
  - "[[Lecture 08112023131119]]"
  - "[[Lecture 19092024125624]]"
---
# Semantica
---
## Introduzione
> La **semantica** di un linguaggio è la parte della linguistica che attribuisce e studia il _significato delle parole_, degli _insiemi di parole_, delle _frasi_ e dei _testi_, e quindi la relazione tra segni ([[Sintassi|sintassi]]) e significato.

Per analizzare la correttezza di una frase da un punto di vista semantico è necessario:
1. _sapere a quale linguaggio la frase appartiene_;
2. _su quale linguaggio basarmi per dare significato_ (tale linguaggio dev'essere noto, cioè non dev'essere a sua volta spiegato).

Nel _linguaggio naturale_ questo è il modo in cui funziona la traduzione: per capire la semantica di una frase inglese c'è bisogno di un traduttore che la traduca in italiano di cui già nativamente comprendiamo la semantica.

Nel _linguaggio artificiale_ questo avviene quando si vuole eseguire uno script scritto in un linguaggio di programmazione che dev'essere semanticamente compreso dal calcolatore attraverso un traduttore ([[Interprete|interprete]] o [[Compilatore|compilatore]]).

Nel contesto della logica la **semantica è una [[Funzione matematica|funzione]] che associa a ogni [[Connotazione|connotazione]] una [[Denotazione|denotazione]] in un [[Dominio di interpretazione|dominio di interpretazione]] fissato**.

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