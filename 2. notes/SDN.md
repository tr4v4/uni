---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 06-04-2025 16:32:24
links:
  - "[[Lecture 17032025095233]]"
---
# SDN
---
## Introduzione
> Il **SDN** (_Software-Defined Networking_) è un'architettura di [[Rete|rete]] che consente di _centralizzare il controllo e la sua gestione attraverso software_.

L'idea di base e' che ogni [[Router|router]] della rete contenga una _local flow table_, calcolata da un _supervisore centrale_.
![[sdn.png]]

Un software/standard/protocollo che consente di realizzare SDN e' [[OpenFlow]]. Questo definisce delle regole di gestione dei pacchetti, definendo in ogni local flow table:
- _pattern_, su cui fare match (un po' come le regex)
- _azioni_, associati ai match dei pattern
- _priorità_
- _contatori_

![[openflow-table.png]]

La combinazione **match+action** consente di unificare diversi ruoli su un singolo dispositivo:
- _router_
	- match: longest destination IP prefix;
	- action: forward;
- _switch_
	- match: destination MAC address;
	- action: forward or flood;
- _firewall_
	- match: source/destination IP address and port;
	- action: permit or deny;
- _NAT_
	- match: source/destination IP address and port;
	- action: rewrite address and port;

## Referenze