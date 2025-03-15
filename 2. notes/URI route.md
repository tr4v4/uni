---
tags:
  - category/note
  - status/finished
  - topic/tecnologie-web
date: 24-09-2024 18:29:10
links:
  - "[[Lecture 19092024151357]]"
---
# URI route
---
## Introduzione
> La **route** di una [[Risorsa|risorsa]] [[Web|web]] è l'associazione tra essa e il `path` di un [[URI]], gestita da un server web.

La route può avvenire secondo due modalità:
- _managed route_: il server associa ogni URI a una risorsa o attraverso un file system locale (statico) o generate attraverso una computazione (dinamico)
- _file-system route_: il server è un libro aperto, il file-system è in diretta associazione (1:1) all'URI

<u>Nota bene</u>: nel _managed route_ anche se c'è l'associazione con il file system locale, a posteriori c'è un controllo che restringe gli URI a cui il server può rispondere, rendendo nascosti o non disponibili/raggiungibili certi file. Per cui, solitamente, questo route è sempre preferito al _file-system route_.

## Referenze