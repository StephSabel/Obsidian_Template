---
company: "[[My Company]]"
location: 
title: 
email: 
mobile: 
website: 
linkedin: 
birthday: 
aliases:
---
## Notes

- 


## Reporting

```dataview
TASK
WHERE reporting = [[]] AND (!completed OR completion >= date(today) - dur(30 d))
```

## Agenda

```dataview
TASK
WHERE agenda = [[]] AND (!completed OR completion >= date(today) - dur(1 d))
```


## Delegated Tasks

```dataview
TASK
WHERE delegated = [[]] AND (!completed OR completion >= date(today) - dur(1 d))

```

## Meetings

```dataview
TABLE dateformat(date(date, "yy-MM-dd"), "dd\. MMMM yy") as Date, summary AS "Summary"
FROM "Journal/Meetings" where contains(attendees, [[]])
SORT date DESC
```