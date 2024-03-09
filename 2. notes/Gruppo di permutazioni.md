---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 30-12-2023 13:04:29
links:
  - "[[Lecture 14122023092114]]"
---
# Gruppo di permutazioni
---
## Introduzione
> Sia $Perm(\mathbb{A})$ l'insieme di tutte le [[Permutazione|permutazioni]] di un insieme $\mathbb{A}$ (chiamato anche gruppo simmetrico su $\mathbb{A}$), allora
> $$(Perm(\mathbb{A}), \circ, id, \cdot^{-1})$$
> è un [[Gruppo|gruppo]] chiamato **gruppo delle permutazioni di $\mathbb{A}$**, dove:
> - $id: \mathbb{A} \to \mathbb{A}$ è la [[Funzione identità|funzione identità]], quindi la permutazione che funge da [[Elemento neutro|elemento neutro]];
> - prese $\pi_{1}$ e $\pi_{2}$ permutazioni di $\mathbb{A}$, anche la loro combinazione $\pi_{1} \circ \pi_{2}$ lo è (quindi $Perm(\mathbb{A})$ _chiuso_ rispetto a $\circ$);
> - presa $\pi$ una permutazione di $\mathbb{A}$, anche $\pi^{-1}$ lo è (quindi $\pi \circ \pi^{-1} = id$).

### Esempio
Il cubo di Rubik è un gruppo di permutazione sulle possibili permutazioni dell'insieme di $6 \times 9 = 54$ celle: _possiamo infatti pensare ogni sua mossa a una permutazione da uno stato del cubo all'altro_. Tali permutazioni, tuttavia, devono rispettare alcuni criteri riguardanti la conformazione del cubo: di fatto la cella centrale di ogni faccia non può mai cambiare, perciò sarà sempre mappata a se stessa (_identità_) in ogni permutazione.

## Importanza
Storicamente i gruppi di permutazioni sono stati la prima famiglia di gruppi ad essere studiata sistematicamente. In particolare il matematico francese [[Evariste Galois]] [[Teoria di Galois|teorizzò]] una _proprietà che lega i polinomi al gruppo di permutazioni sull'insieme delle sue radici_.

Il teorema più importante dei gruppi è il [[Teorema di Cayley|teorema di Cayley]].

## Referenze