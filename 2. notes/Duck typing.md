---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 24-09-2025 23:50:53
links:
  - "[[Lecture 16042025110927]]"
---
# Duck typing
---
## Introduzione
> Il [[Type checking|tipaggio]] **duck typing** e' la forma piu' utilizzata di [[Tipaggio dinamico|tipaggio dinamico]] (quindi a run-time), spesso nei linguaggi [[Interprete|interpretati]], e _consiste nel controllare se un dato valore supporta gli operatori previsti dal programma_.

```C
sum( p ){ return p.x + p.y }
loc( p ){ return p.x % p.y % p.z }

c = { x: 15, y: 25, z: 63 }
s = { x: 64, y: 17 }

sum( c ) // 40
sum( s ) // 81
loc( c ) // 15
loc( s ) // Error: s has no field 'z'
```

## Referenze