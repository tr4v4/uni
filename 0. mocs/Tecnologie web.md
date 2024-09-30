---
tags:
  - "#category/moc"
  - "#status/finished"
  - topic/tecnologie-web
date: 16-09-2024 10:38:09
---
# Tecnologie web
---
## Lezioni
### Ultima lezione
```dataview
TABLE
WITHOUT ID file.link AS Lezione, file.inlinks AS Note
FROM #category/lecture AND #topic/tecnologie-web
SORT file.ctime DESC
LIMIT 1
```

### Lista
```dataview
TABLE
WITHOUT ID file.link AS Lezione, date AS Data
FROM #category/lecture AND #topic/tecnologie-web
SORT file.ctime DESC
```

### Da processare
```dataview
TABLE
WITHOUT ID file.link as Lezione, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing") AS Status
FROM #category/lecture AND #topic/tecnologie-web AND (#status/pending OR #status/ongoing)
SORT date DESC
```

## Note
- Argomenti
	- [[Web]], [[HTTP]], [[REST]], [[URI]], Codifica dei caratteri/contenuti
	- Web dei documenti: XML, WCAG, CSS, HTML, Markup
	- Web dei programmi:
		- client-side: JS, JS framework, framework a componenti come Angular, React e Vue
		- server-side: LAMP, PHP, Python, NodeJs
	- Web dei dati: Linked Data Ontologie, SPARQL, JSON-LD, RDF

```dataview
TABLE
WITHOUT ID file.link AS Note, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing" OR t="#status/finished") AS Status
FROM #category/note AND #topic/tecnologie-web
SORT file.ctime DESC
```

## Referenze
- [virtuale](https://virtuale.unibo.it/course/view.php?id=65831)
- [dynamik]()
- eserciziari