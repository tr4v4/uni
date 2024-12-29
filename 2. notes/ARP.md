---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 13-12-2024 17:21:54
links:
  - "[[Lecture 20112024140334]]"
---
# ARP
---
## Introduzione
> **ARP** (_Address Resolution Protocol_) è un [[Protocollo di rete|protocollo]] sia del [[Livello MAC-LLC|livello MAC-LLC]] che del [[Livello rete|livello rete]], che all'interno di una [[Rete|rete]] _permette di risalire all'[[Indirizzo MAC|indirizzo MAC]] di un host di cui si conosce l'[[Indirizzo IP|indirizzo IP]]_.

## Idea
Mettiamo caso che un [[Router|router]] riceva un pacchetto dall'esterno che debba essere inoltrato a un host appartenente alla sua [[LAN|rete locale]]. Lui **conosce l'indirizzo IP del destinatario, ma non il suo MAC**: _come fa ad inviare il frame_?

Lo stesso problema si ripresenta anche negli host: un host vuole inviare un pacchetto a un destinatario fuori dalla sua rete, conosce l'indirizzo IP del router (_default gateway_) ma non il suo MAC; sempre un host vuole inviare un pacchetto a un destinatario all'interno della sua rete, di cui conosce l'IP ma non il MAC.

## Funzionamento
Di base ogni host salva in una tabella (detta tabella ARP) le associazioni IP-MAC. Ogni qualvolta questo non conosca l'indirizzo MAC di un destinatario di cui sa l'IP, **invia un frame broadcast** (`FF:FF:FF:FF:FF:FF`) **a cui risponde solo il destinatario interessato** (con quell'IP), **comunicando il suo MAC**. Il mittente, quindi, salva nella sua tabella ARP questa associazione.

Una volta la tabella ARP veniva riempita manualmente... oggi il _protocollo prevede un aggiornamento automatico periodico_.

## Comando
Nei [[Sistema operativo|sistemi operativi]] è possibile conoscere la tabella ARP salvata con il comando `arp -a`.

## Referenze
- [[RARP]]