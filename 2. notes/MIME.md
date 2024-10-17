---
tags:
  - category/note
  - status/finished
  - topic/tecnologie-web
date: 13-10-2024 13:34:05
links:
---
# MIME
---
## Introduzione
> **MIME** (_Multipurpose Internet Mail Extensions_) è un'estensione che ridefinisce il formato del corpo di un messaggio [[SMTP]] per permettere:
> - messaggi di testo in altri set di caratteri al posto di [[ASCII]];
> - un insieme estensibile di formati per messaggi non testuali;
> - messaggi multi-parte;
> - header con set di caratteri diversi da ASCII.

## Funzionamento
Il messaggio formattato secondo MIME viene scomposto da un preprocessore in più messaggi SMTP. Ricevuti, questi frammenti vengono decodificati e riaccorpati a formare il messaggio originale.

## Servizi
I messaggi MIME sono identificati da un **ContentType** che definisce il tipo di dati del messaggio, consentendo al ricevente di decodificarli nel modo corretto.

Per messaggi multi-tipo vengono create dei sottomessaggi MIME per ciascuna parte.

### Header
Gli header introdotti da MIME sono:
- _Content-Type_, il tipo MIME del contenuto;
- _Content-Transfer-Encoding_, il tipo di codifica utilizzata per trasmettere i dati (es. _[[Base64|base64]]_ o _Quoted printable_ che serve per la trasmissione di dati che contengono grosse quantità di byte nel set ASCII, e solo poche eccezioni).

## Referenze