---
up: "[[Map=Paper]]"
---
```dataview
TABLE date, publication, p-date
FROM #Paper 
WHERE file.name != "Paper Template"
SORT file.name ASC
```
