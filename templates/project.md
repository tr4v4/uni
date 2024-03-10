---
tags:
  - category/project
  - status/pending
  - topic/
date: <%tp.file.creation_date("DD-MM-YYYY HH:mm:ss")%>
deadline:
---
# <%tp.file.title%>
---
## Kanban

## Reports
```dataview
LIST
WHERE
	contains(file.folder, this.file.folder)
	AND
	contains(file.tags, "#category/report")
```

## Referenze