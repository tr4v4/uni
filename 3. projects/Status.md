---
tags:
  - "#category/moc"
  - "#status/pending"
date: 30-09-2023 20:47:49
---
# Status
---
## Deadlines
```dataview
TABLE
WITHOUT ID file.link AS Progetti, deadline AS Deadline
FROM #category/project
WHERE contains(file.folder, this.file.folder)
SORT deadline ASC
```

## Referenze