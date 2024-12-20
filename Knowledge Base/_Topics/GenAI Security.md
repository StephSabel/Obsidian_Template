---
topics:
  - "[[GenAI Security]]"
---


# Sources & External Links

- https://genai.owasp.org/


# Notes

- This is a topic I work on whenever I have some time


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
