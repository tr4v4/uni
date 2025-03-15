---
tags:
  - category/note
  - status/finished
  - topic/tecnologie-web
date: 13-10-2024 14:28:07
links:
  - "[[Lecture 26092024150810]]"
---
# SGML
---
## Introduzione
> **SGML** (_Standard Generalized Markup Language_) è un meta-linguaggio di [[Markup|markup]] non proprietario, descrittivo, gerarchico, strutturato, leggibile. In particolare è uno standard per la creazione di linguaggi di markup.

## Documento
Un documento SGML si compone di:
1. _dichiarazione SGML_ - identifica la lunghezza dei nomi degli elementi, la [[Codifica dei caratteri|codifica dei caratteri]] utilizzata; è lunga di solito centinaia di righe, e se omessa viene usata quella standard (**RCS**, _Reference Concrete Syntax_);
2. _dichiarazione DOCTYPE_ - si va a definire la metasintassi, a descrivere il vocabolario e le regole di correttezza del linguaggio di markup;
3. _istanza del documento_ - l'effettiva scrittura del documento nel linguaggio di markup definito nel DOCTYPE.

### Componenti
Un'istanza di SGML contiene una varietà di componenti, quali:
- elementi (tag + contenuto)
- attributi (informazioni aggiuntive sugli elementi)
- entità (frammenti di documento memorizzati e richiamabili all'interno dello stesso)
- testo (anche chiamato `#PCDATA`)
- commenti
- processing instructions

## Istanze conosciute
- [[XML]]
- [[HTML]]

## Referenze