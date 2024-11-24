---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 19-11-2024 19:47:10
links:
  - "[[Lecture 25102024131215]]"
---
# Classi di rete
---
## Introduzione
Gli [[Indirizzo IP|indirizzi IP]] ([[IPv4|v4]]) si classificano in 3 classi principali:
- **Classe A** - `0xxxxxxx-yyyyyyyy-yyyyyyyy-yyyyyyyy`
	- _network number_: 1. - 126. (`0xxxxxxx`)[^1]
	- _host number_: 0.0.1 - 255.255.255 (`yyyyyyyy-yyyyyyyy-yyyyyyyy`)
	- 16 milioni di host, sono indirizzi usati dagli _internet provider_
- **Classe B** - `10xxxxxx-xxxxxxxx-yyyyyyyy-yyyyyyyy`
	- _network number_: 128.0. - 191.255. (`10xxxxxx-xxxxxxxx`)
	- _host number_: 0.1 - 255.255 (`yyyyyyyy-yyyyyyyy`)
- **Classe C** - `110xxxxx-xxxxxxxx-xxxxxxxx-yyyyyyyy`
	- _network number_: 192.0.0. - 223.255.255. (`110xxxxx-xxxxxxxx-xxxxxxxx`)
	- _host number_: 1 - 254 (`yyyyyyyy`)[^2]

<u>Osservazione</u>: _nessuna classe di rete è un prefisso dell'altra_[^3].

## Referenze
[^1]: `127` è _indirizzo di loopback_, mentre `0` non viene usato
[^2]: `255` è l'_indirizzo di broadcast_, mentre `0`
[^3]: proprio come la [[Codifica di Huffman|codifica di Huffman]]