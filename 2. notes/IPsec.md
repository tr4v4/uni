---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 09-03-2025 16:48:33
links:
  - "[[Lecture 25022025152711]]"
---
# IPsec
---
## Introduzione
> **IPsec** e' un layer software appartenente al [[Modello ISO-OSI|modello ISO-OSI]] che si colloca tra il [[Livello rete|livello rete]] e il [[Livello trasporto|livello trasporto]], che _offre meccanismi di cifratura degli [[Indirizzo IP|indirizzi IP]] e di tutto cio' che viene incapsulato nel livello trasporto e nel [[Livello applicazione|livello applicazione]]_.

## Funzionamento
Fondamentalmente IPsec consente di creare un **tunnelling**, **mantenendo visibili degli indirizzi IP esterni per consentire una corretta navigazione sui [[Router|router]], ma mascherando i reali indirizzi IP** (+ trasporto e applicazione) attraverso tecniche di [[Crittografia|cifratura]].

In breve, IPsec garantisce:
- integrità dei dati
- autenticazione
- prevenzione al replay attack
- confidenzialità

![[ipsec-vpn.png]]

### Modalita'
Esistono due modalita' di utilizzo dell'IPsec:
- **transport mode** --> sono i singoli host a incapsulare i dati in pacchetti IPsec, e' il meccanismo delle moderne [[VPN]];
- **tunnelling mode** --> sono i router di confine (da rete locale a [[Internet|internet]]) che aggiungono gli header IPsec;

### Modelli
Esistono due implementazioni dell'IPsec:
- **AH** (Authentication Header) --> più snello, cripta meno, ma non supporta confidenzialità;
- **ESP** (Encapsulation Security Protocol) --> supporta tutte le misure di sicurezza;

Il tunnelling con ESP e' il sistema piu' comune di utilizzo di IPsec.

## Datagramma
Un pacchetto IPsec (tunnelling + ESP) si compone nel seguente modo:
![[ipsec-tunnelling-esp-datagram.png]]

## Referenze