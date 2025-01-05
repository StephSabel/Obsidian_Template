---
website: 
aliases:
---

tags:: [[Companies]]

## Projects

```dataview
TABLE title as Title
FROM "Entities/Projects"
WHERE contains(company, [[]])
SORT file.name
```

## Contacts

```dataview
TABLE title as Title
FROM "Entities/People"
WHERE contains(company, [[]])
SORT file.name
```

 
## Client Development

```dataview
TABLE dateformat(date(date, "yy-MM-dd"), "dd\. MMMM yy") as Date, summary as Summary, companies as Companies
FROM "Journal/Meetings" 
where project = [[_Client Development]] AND (contains(companies, this.file.name) OR (contains(companies, [[]])))
SORT file.cday DESC
```

## Meetings with Company Participation

```dataview
TABLE dateformat(date(date, "yy-MM-dd"), "dd\. MMMM yy") as Date, summary as Summary, companies as Companies
FROM "Journal/Meetings" 
where project != [[_Client Development]] AND (contains(companies, this.file.name) OR (contains(companies, [[]])))
SORT file.cday DESC
```