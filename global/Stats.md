---
created_at: 2023-08-12, 5:58:16 pm
updated_at: 2023-08-18, 8:58:54 pm
---
# Stats
## Common
```dataview
table file.size as "Size", file.mtime as "Modified"
from "src"
where !contains(file.folder, "attachments")
and !contains(file.name, "excalidraw")
and file.ext = "md"
sort file.size desc
```

## Drawings

```dataview
table length(rows) as "Drawings"
from "src"
flatten file.outlinks as out
where contains(out.file.name, "excalidraw")
group by file.name as File
sort out desc
```

## Tasks
```dataview
task
from "src"
group by file.name
```