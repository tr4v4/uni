---
tags:
  - "#category/moc"
  - "#status/finished"
  - topic/reti-di-calcolatori
date: 16-09-2024 10:43:40
---
# Reti di calcolatori
---
## Lezioni
### Ultima lezione
```dataview
TABLE
WITHOUT ID file.link AS Lezione, file.inlinks AS Note
FROM #category/lecture AND #topic/reti-di-calcolatori
SORT file.ctime DESC
LIMIT 1
```

### Lista
```dataview
TABLE
WITHOUT ID file.link AS Lezione, date AS Data
FROM #category/lecture AND #topic/reti-di-calcolatori
SORT file.ctime DESC
```

### Da processare
```dataview
TABLE
WITHOUT ID file.link as Lezione, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing") AS Status
FROM #category/lecture AND #topic/reti-di-calcolatori AND (#status/pending OR #status/ongoing)
SORT date DESC
```

## Note
- Argomenti

```dataview
TABLE
WITHOUT ID file.link AS Note, filter(file.tags, (t) => t="#status/pending" OR t="#status/ongoing" OR t="#status/finished") AS Status
FROM #category/note AND #topic/reti-di-calcolatori
SORT file.ctime DESC
```

## Referenze
- [virtuale]()
- [dynamik]()
- eserciziari