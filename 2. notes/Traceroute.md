---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 13-12-2024 17:07:45
links:
  - "[[Lecture 15112024133341]]"
  - "[[Lecture 20112024140334]]"
---
# Traceroute
---
## Introduzione
> **Traceroute** è un'applicazione preinstallata nella maggior parte dei [[Sistema operativo|sistemi operativi]] che _individua i [[Router|router]] attraverso cui passa un pacchetto per raggiungere una destinazione_, mediante messaggi [[ICMP]].

## Funzionamento
Richiamando il comando `traceroute <IP>` vengono inviati in sequenza una serie di messaggi ICMP, su distanze ogni volta maggiori. Questi, al momento del ritorno, comunicano l'[[Indirizzo IP|indirizzo]] dell'_hop_ (router di passaggio) su cui si sono fermati.

Per poter implementare il meccanismo delle distanze, all'interno del messaggio ICMP viene definito il [[TTL]] (_Time To Live_), un campo che indica il numero massimo di host che può attraversare il pacchetto prima di essere scartato. Così, **ogni router su cui passa il pacchetto decrementa il TTL**; nel momento in cui arriva **a 0 il pacchetto viene scartato e al mittente viene inviato un ICMP di errore come risposta**.

### Limiti
Così facendo, _a causa dell'incostanza delle tabelle di instradamento dei routing_, il percorso dei pacchetti ICMP potrebbe non essere stabile. **Non viene infatti garantito un percorso "verosimile" dei router attraversato**. Questa garanzia si ha nel momento in cui la [[Topologia di rete|rete è ad albero]]: in tal caso la strada percorsa è sempre una sola, e infatti le tabelle dei router non necessitano di particolari [[Protocollo di routing|algoritmi di routing]].

Inoltre, esistono dei **router anonimizzati**, che nascondono le loro informazioni (come l'IP).

## Referenze