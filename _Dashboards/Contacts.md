## Contacts
```dataview
TABLE company as Company, title as Title
FROM "Entities/People"
WHERE file.name != this.file.name
SORT company
```


