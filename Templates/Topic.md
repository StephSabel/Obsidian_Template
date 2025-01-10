---
topics:
  - "[[<% tp.file.title %>]]"
---


# Sources & External Links

- 


# Notes

- 


# Tasks

```dataview  
TASK  
FROM "Journal"  
WHERE topics = [[]] AND !delegated AND !completed AND status != "-" AND status != ">"  
```


# Meetings

```dataview
TABLE dateformat(date(date, "yy-MM-dd"), "dd MMM yy") as Date, summary as Summary
FROM "Journal/Meetings" where (contains(topics, this.file.name) OR contains(topics, [[]]))
SORT file.cday DESC
```


# Other Pages

```dataview
LIST 
FROM -"Journal/Meetings" AND -"Knowledge Base/_Topics" 
where (contains(topics, this.file.name) OR contains(topics, [[]]))
SORT file.cday DESC
```
