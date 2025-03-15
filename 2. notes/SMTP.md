---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 09-03-2025 09:18:54
links:
  - "[[Lecture 20122024133953]]"
---
# SMTP
---
## Introduzione
> L'**SMTP** (**Simple Mail Transfer Protocol**) e' il _[[Protocollo|protocollo]] principale usato per l'invio di email di [[Posta elettronica|posta elettronica]]_.

## Caratteristiche
Si basa su [[TCP]], e usa la [[Porta|porta]] `25`. Viene **usato da un mail server per trasferire un messaggio di posta elettronica su un altro mail server**. Il tipo di connessione instaurato con SMTP e' _persistente_ (piu' risorse sono trasferite in un'unica connessione TCP). La fine del messaggio email e' determinato dalla sequenza di caratteri `CRLF.CRLF`.

Il formato della email e' determinato da uno standard, in cui si specifica _mittente_, _destinatario_ e _oggetto_. Questi campi sono interni alla mail, ma nello scambio tra server mail vengono specificati con appositi comandi (vedi di seguito) sempre mittente e destinatario.

## Funzionamento
Lo scambio di email si compone in 3 fasi:
1. handshaking
2. trasferimento
3. chiusura

![[smtp-interaction.png]]

E' importante ricordare che l'**SMTP supporta solo messaggi in [[ASCII]] 7 bit**, per cui per inviare contenuti multimediali o codificati in un altro [[Codifica dei caratteri|set di caratteri]], e' necessario adottare il [[MIME]].

## Referenze