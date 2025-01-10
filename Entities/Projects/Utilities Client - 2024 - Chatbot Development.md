---
company: "[[Utilities Client]]"
project: "[[Utilities Client - 2024 - Chatbot Development|NewBot]]"
aliases:
  - NewBot
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