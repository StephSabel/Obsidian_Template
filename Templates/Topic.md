---
topics:
  - "[[<% tp.file.title %>]]"
---


# Sources & External Links

- 


# Notes

- 


# Meetings

```dataview
TABLE dateformat(date(date, "yy-MM-dd"), "dd\. MMMM yy") as Date, summary as Summary
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
