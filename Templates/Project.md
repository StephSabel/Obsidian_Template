---
company: "[[{{VALUE:Client}}]]"
project code: 
start: 
end: 
status: 
project team: 
stakeholders: 
topics: 
project: 
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
TABLE dateformat(date(date, "yy-MM-dd"), "dd MMM yy") as Date, summary as Summary
FROM "Journal/Meetings" where project = [[]]
SORT date DESC
```