```dataview
TABLE
FROM "Entities/Companies"
WHERE file.name != this.file.name
SORT company
```
