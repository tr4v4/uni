---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 28-09-2025 20:24:06
links:
  - "[[Lecture 23042025111218]]"
---
# Tipi monadici
---
## Introduzione
### Tipo opzione
E' utile per gestire in maniera strutturata [[Puntatori|puntatori]] nulli (abitante `null`).
Mescolano [[Generics|tipi parametrici]] con [[Tipo somma|tipi somma]]:
```rust
type Maybe<T>: Some<T> + None
```

### Tipo risultato
E' un raffinamento dei tipi opzione, dove usiamo i tipi polimorfi e somma per distinguere tra il risultato di un calcolo e un'esecuzione errata.
```rust
type Result<T, E> : Ok<T> + Err<E>
```
E' un'alternativa alla gestione delle [[Eccezione|eccezioni]].

## Referenze