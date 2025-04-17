---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 13-12-2024 17:40:28
links:
  - "[[Lecture 20112024140334]]"
  - "[[Lecture 22112024130956]]"
  - "[[Lecture 17032025095233]]"
---
# DHCP
---
## Introduzione
> **DHCP** (_Dynamic Host Configuration Protocol_) è un [[Protocollo di rete|protocollo]] di [[Livello rete|livello rete]] _che permette l'assegnazione degli [[Indirizzo IP|indirizzi IP]] in modo dinamico_, servendosi di un [[Server DHCP|server DHCP]].

Il servizio DHCP fa parte della categoria di strumenti "_plug-and-play_", in cui non è necessaria una fase di configurazione manuale per poter accedere al mezzo (in questo caso la rete). Infatti è parecchio usato in reti [[Wi-Fi]].

## Funzionamento
Il protocollo DHCP si basa su un modello client-server, in cui il client richiede un indirizzo IP e il server lo assegna. Il processo di assegnazione degli indirizzi IP avviene in 4 fasi:
1. **DHCP discover** --> il client invia un messaggio di broadcast per cercare un server DHCP disponibile;
2. **DHCP offer** --> il server DHCP risponde con un messaggio di offerta, contenente un indirizzo IP disponibile e altre informazioni di configurazione;
3. **DHCP request** --> il client invia un messaggio di richiesta al server DHCP per accettare l'offerta ricevuta;
4. **DHCP acknowledgment** --> il server DHCP invia un messaggio di conferma al client, completando la configurazione;

## Referenze