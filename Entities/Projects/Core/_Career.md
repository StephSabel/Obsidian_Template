---
company: "[[My Company]]"
start: 
stakeholders:
  - "[[Jane Boss]]"
project: "[[_Career]]"
aliases: 
---

# Notes




# Tasks
## Recurring tasks

### Time reporting

- [x] Finish time reporting 🔁 every month on the 1st 📅 2024-12-01 ✅ 2024-12-20
- [x] Finish time reporting 🔁 every month on the 1st 📅 2025-01-01 ✅ 2025-01-05
- [ ] Finish time reporting 🔁 every month on the 1st 📅 2025-02-01


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
SORT file.cday DESC
```