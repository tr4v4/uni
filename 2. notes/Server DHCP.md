---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 14-12-2024 14:25:59
links:
  - "[[Lecture 20112024140334]]"
  - "[[Lecture 22112024130956]]"
---
# Server DHCP
---
## Introduzione
> Un **server DHCP** è un _[[Server|server]] che implementa il servizio di assegnazione dinamico degli [[Indirizzo IP|indirizzi IP]] [[DHCP]]_.

## Funzionamento
Il _server DHCP deve avere un indirizzo IP statico_, riferito manualmente (o ricavato autonomamente) agli host che vogliono usufruire del servizio. Questo dispone di un **blocco di _host number_ liberi per la sua rete (pool)**, che _assegna ad ogni host connesso alla rete che ne fa richiesta_ (scelta decisa durante la configurazione della rete).

L'indirizzo offerto dal server viene associato a un **tempo di lease**, una durata temporale di validità dell'indirizzo (configurabile nel DHCP): _poco prima che il tempo scada, il server invia un [[Ping|ping]] all'host per vedere se è ancora connesso, e se lo è rinnova il lease, altrimenti lo rilascia_.

Infine, il server DHCP mantiene l'associazione tra gli indirizzi IP assegnati e gli [[Indirizzo MAC|indirizzi MAC]] ([[ARP]]).

## Referenze