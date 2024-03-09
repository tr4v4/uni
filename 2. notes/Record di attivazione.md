---
tags:
  - category/note
  - status/finished
  - topic/architettura-degli-elaboratori
date: 05-11-2023 22:34:02
links:
  - "[[Lecture 02112023130607]]"
---
# Record di attivazione
---
## Introduzione
Nel contesto dell'[[Invocazione di procedura|invocazione di procedura]], è necessario salvare una serie di informazioni necessarie all'esecuzione della [[Funzione informatica|funzione]]/procedura in uno spazio salvato in [[Stack|stack]] chiamato **record di attivazione**.

## Principio di funzionamento
Esso stesso è strutturato come una _pila_, in modo tale da poter essere "impilati" uno sull'altro nello stack. L'idea di base è comprendere che **quando termina l'esecuzione di una procedura, il suo record di attivazione deve "passare la palla" alla procedura che l'ha invocata**. Nel caso, in particolare, della [[Ricorsione|ricorsione]], una procedura invoca se stessa un numero indefinito di volte, fino a terminare: _l'ultima procedura invocata dovrà restituire il controllo a quella precedente, e così via fino a tornare al processo chiamante_.

Per tener traccia, all'interno dello stack, del record di attivazione attualmente in esecuzione, vi è un registro specializzato chiamato **Frame Pointer** ([[FP]]).

## Composizione
Un recordo di attivazione si compone di:
- _parametri di invocazione_ --> i cosiddetti [[Funzione informatica#Invocazione|parametri attuali]]
- _indirizzo di ritorno_ --> l'indirizzo del [[PC]] al momento dell'invocazione della procedura, per poter rimettere in esecuzione il chiamante
- _vecchio frame pointer_ --> per ripristinare l'FP al momento del ritorno al chiamante
- _variabili locali_ --> dichiarate nella [[Funzione informatica#Definizione|definizione della funzione]]

## Referenze