---
up:
  - "[[Paper/Maps/Paper List]]"
---
```dataview
TABLE date, publication, p-date
FROM #Paper-Deep
WHERE file.name != "Paper Template"
SORT file.name ASC
```
