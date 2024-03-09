---
tags:
  - category/note
  - status/finished
  - topic/programmazione
date: 03-12-2023 16:07:13
links:
  - "[[Lecture 29112023092601]]"
---
# Albero binario di ricerca
---
## Introduzione
> Un **albero binario di ricerca** è un [[Albero binario|albero binario]] cui _nodi sono ordinati in modo crescente da sinistra a destra_. Si ha che ogni nodo centrale è maggiore di tutti i nodi del sottoalbero sinistro e minore di tutti i nodi del sottoalbero destro.

![[albero-binario-di-ricerca.png]]

## Operazioni

### Ricerca
L'algoritmo di ricerca di un valore all'interno di tali alberi si riduce ad una versione bidimensionale della [[Ricerca dicotomica|ricerca binaria]] degli [[Array|array]]:
```cpp
bool search(btree *t, int n) {
	if (t == NULL) return false;
	else if (t->val == n) return true;
	else if (t->val > n) return search(t->ltree, n);
	else return search(t->rtree, n);
}
```

La [[Complessità computazionale|complessità compiutazionale]] diventa, nel caso peggiore, equivalente al cammino più lungo dell'albero.

Stranamente anche la versione iterativa della ricerca ne esce semplificata dalla composizione dell'albero.

### Inserimento
Per inserire un nuovo elemento in un albero di ricerca si implementa il seguente algoritmo [[Ricorsione|ricorsivo]]:
```cpp
btree *t_insert(btree *t, int n) {
	if (t == NULL) {
		btree *tmp = new btree;
		tmp->val = n;
		tmp->ltree = NULL;
		tmp->rtree = NULL;
	} else if (t->val > n) t->ltree = t_insert(t->ltree, n);
	else t->rtree = t_insert(t->rtree, n);
	return t;
}
```

## Referenze