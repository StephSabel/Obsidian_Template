## Meetings without summary

```dataview
TABLE summary as Summary, dateformat(date(date, "yy-MM-dd"), "dd\. MMMM yy") as Date
FROM "Journal/Meetings"
WHERE !summary OR summary = ""
```


## Meetings without project

```dataview
TABLE summary as Summary, dateformat(date(date, "yy-MM-dd"), "dd\. MMMM yy") as Date
FROM "Journal/Meetings"
WHERE !project
```


## All Meetings

```dataview
TABLE 
summary as Summary, 
dateformat(date(date, "yy-MM-dd"), "dd\. MMMM yy") as Date

FROM "Journal/Meetings"
SORT file.cday DESC
```

