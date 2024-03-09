---
tags:
  - category/note
  - status/finished
  - topic/programmazione
date: 25-10-2023 14:18:58
links:
  - "[[Lecture 24102023100626]]"
---
# Bubble sort
---
## Introduzione
```cpp
void bubble_sort(int v[], int n) {
	for (int i=n-1; i>=0; i--) {
		for (int j=0; j<i-1; j++) {
			if (v[j] > v[j+1])
				swap(v[j], v[j+1]);
		}
	}
}
```

## Referenze