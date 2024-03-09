---
tags:
  - category/note
  - status/finished
  - topic/programmazione
date: 30-11-2023 18:05:47
links:
  - "[[Lecture 28112023101904]]"
  - "[[Lecture 29112023092601]]"
---
# Albero binario
---
## Introduzione
> Un **albero binario** è un tipo di [[Albero informatico|albero]] cui _ogni nodo può essere una foglia oppure diramarsi in un sottoalbero sinistro e un sottoalbero destro_.

![[albero-binario.png]]

Da un punto di vista [[Algebra astratta|algebrico]], l'albero binario è un [[ADT]] definito dalla _tripla_
$$T' ::= \varnothing \ | \ \mathcal{N}(T', \mathbb{N}, T')$$

## Implementazione
Si utilizzano [[Strutture dati|strutture]] con 3 campi:
```cpp
struct btree {
	int val;
	btree *ltree;
	btree *rtree;
};
```

## Operazioni
### Creazione
```cpp
pbtree create_btree(int n) {
	if (n == 0) return(NULL);
	else {
		pbtree t = new btree;
		t->val = rand()%50;
		t->ltree = create_btree(n-1);
		t->rtree = create_btree(n-1);
		return(t);
	}
}
```

### Visita
```cpp
// Visita prefissa
void pre_visit(pbtree t) {
	if (t != NULL) {
		cout << t->val << "\t";
		visit(t->ltree);
		visit(t->rtree);
	}
}

// Visita infissa
void in_visit(pbtree t) {
	if (t != NULL) {
		visit(t->ltree);
		cout << t->val << "\t";
		visit(t->rtree);
	}
}

// Visita postfissa
void post_visit(pbtree t) {
	if (t != NULL) {
		visit(t->ltree);
		visit(t->rtree);
		cout << t->val << "\t";
	}
}
```

### Ricerca
La ricerca di un valore in un albero, _per quanto elegante_, se implementata [[Ricorsione|ricorsivamente]] ha una **[[Complessità computazionale|complessità compiutazionale]] pessima**: di fatto _bisogna provare tutte le possibili strade dell'albero_, esattamente come avviene per la ricerca in un array disordinato.
```cpp
bool search(btree *t, int n) {
	if (t == NULL) return false;
	else if (t->val == n) return true;
	else return search(t->ltree, n) || search(t->rtree, n);
}
```

Solitamente, infatti, la ricerca si computa per [[Albero binario di ricerca|alberi binari di ricerca]].

## Osservazioni
Il numero di nodi di un albero binario di profondità $n$ è pari a
$$\sum\limits_{i = 0}^{n} 2^{i} = 2^{n+1} - 1$$

## Referenze