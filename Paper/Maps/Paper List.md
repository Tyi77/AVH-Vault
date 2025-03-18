---
up: "[[Map=Paper]]"
---
```dataview
TABLE p-date, publication, date
FROM #Paper 
WHERE file.name != "Paper Template"
SORT p-date DESC
// SORT date DESC
```
