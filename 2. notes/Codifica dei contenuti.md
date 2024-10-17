---
tags:
  - category/note
  - status/finished
  - topic/tecnologie-web
date: 13-10-2024 13:21:07
links:
---
# Codifica dei contenuti
---
## Introduzione
Il problema nasce dal protocollo [[SMTP]], che pone i seguenti limiti per l'invio e la ricezione di email:
- la lunghezza massima del messaggio è di 1 MB;
- i caratteri accettati sono solo [[ASCII]] a 7 bit;
- ogni messaggio deve contenere una sequenza `CRLF` ogni 1000 caratteri o meno;

Questi vincoli impediscono la trasmissione di documenti binari, infatti:
- un file binario usa tutti i 256 tipi di byte;
- un file binario può facilmente essere più lungo di 1 MB;
- in un file binario la sequenza `CRLF` è una sequenza come tutte le altre, e può esserci o mancare senza vincoli --> introdurla artificialmente può corrompere il file.

L'estensione [[MIME]] permette di bypassare questi limiti.

## Referenze