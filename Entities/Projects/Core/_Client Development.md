---
company: "[[My Company]]"
project: "[[_Client Development]]"
aliases: 
---

# Notes

- 


# Tasks
## Recurring tasks




## My tasks 

```dataview
TASK
FROM "Journal"
WHERE project = [[]] AND !delegated AND !completed AND status != "-" AND status != ">"
```


## Delegated Tasks

```dataview
TASK
FROM "Journal"
WHERE project = [[]] AND delegated AND !completed AND status != "-" 
GROUP BY delegated
```

# Meetings

```dataview
TABLE dateformat(date(date, "yy-MM-dd"), "dd MMM yy") as Date, summary as Summary, companies as Companies
FROM "Journal/Meetings" where project = [[]]
SORT file.cday DESC
```