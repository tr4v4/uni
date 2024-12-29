---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 13-12-2024 16:57:41
links:
  - "[[Lecture 15112024133341]]"
---
# Ping
---
## Introduzione
> **Ping** è un'applicazione preinstallata nella maggior parte dei [[Sistema operativo|sistemi operativi]] che _verifica la connettività tra due host_, mediante messaggi [[ICMP]].

## Funzionamento
Richiamando il comando `ping <IP>` su un host, vengono inviate richieste ICMP all'host identificato dall'[[Indirizzo IP|indirizzo IP]] `IP`, che se esiste ed è raggiungibile risponde con `echo`.

Ricevuta la risposta dal mittente viene anche calcolato e mostrato il [[RTT]] (_tempo di andata e ritorno_), per misurare le [[Prestazione delle reti|prestazioni della rete]].

## Referenze