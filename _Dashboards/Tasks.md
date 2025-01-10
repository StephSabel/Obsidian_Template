# Scheduled Tasks

```dataview

TABLE WITHOUT ID

regexreplace(regexreplace(Tasks.text, "\[(delegated|project)::.*\]", ""), "📅.*", "") AS Task,

choice(Tasks.due < striptime(date(now)), "⚠️ " + dateformat(Tasks.due, "dd MMM yy") ,dateformat(Tasks.due, "dd MMM yy")) AS "Due Date",

choice(project, project, Tasks.project) AS "Project",

("[[" + file.path + "|🔗]]") AS "Link"

  

FROM -"Knowledge Base" AND -"Templates"

FLATTEN file.tasks AS Tasks

WHERE !Tasks.completed AND !Tasks.reporting AND !Tasks.delegated AND !Tasks.agenda AND Tasks.status != "D" AND Tasks.status != "-" and Tasks.due

SORT Tasks.due ASC

```

# Ongoing Work

```dataview

TABLE WITHOUT ID

regexreplace(regexreplace(Tasks.text, "\[(delegated|project)::.*\]", ""), "📅.*", "") AS Task,

choice(Tasks.start <= striptime(date(now)), "🛫 " + dateformat(Tasks.start, "dd MMM yy") ,dateformat(Tasks.start, "dd MMM yy")) AS "Start Date",

choice(project, project, Tasks.project) AS "Project",

("[[" + file.path + "|🔗]]") AS "Link"

  

FROM -"Knowledge Base" AND -"Templates"

FLATTEN file.tasks AS Tasks

WHERE !Tasks.completed AND !Tasks.delegated AND !Tasks.reporting AND !Tasks.agenda AND Tasks.status != "D" AND Tasks.status != "-" and !Tasks.due AND Tasks.start

SORT Tasks.start ASC

```


# Without due date

```tasks

not done

no due date

no start date

(path does not include Knowledge Base) AND (path does not include Templates)

(description regex does not match /\[delegated/) AND (description regex does not match /\[agenda/)

filter by function task.status.symbol !== "D"

```


# Delegated Tasks

```dataview

TABLE WITHOUT ID

regexreplace(regexreplace(Tasks.text, "\[(delegated|project)::.*\]", ""), "📅.*", "") AS Task,

choice(Tasks.due < striptime(date(now)), "⚠️ " + dateformat(Tasks.due, "dd MMM yy") ,dateformat(Tasks.due, "dd MMM yy")) AS "Due Date",

Tasks.delegated AS Person,

choice(project, project, Tasks.project) AS "Project",

("[[" + file.name + "|🔗]]") AS "Link"

  

FROM -"Knowledge Base" AND -"Templates"

FLATTEN file.tasks AS Tasks

WHERE !Tasks.completed AND !Tasks.reporting AND Tasks.delegated AND !Tasks.agenda AND Tasks.status != "D" AND Tasks.status != "-" and Tasks.due

SORT Tasks.due ASC

```

# Agenda

```dataview

TABLE WITHOUT ID

regexreplace(regexreplace(Tasks.text, "\[(agenda|project)::.*\]", ""), "📅.*", "") AS Task,

choice(Tasks.due, choice(Tasks.due < striptime(date(now)), "⚠️ " + dateformat(Tasks.due, "dd MMM yy") ,dateformat(Tasks.due, "dd MMM yy")), Tasks.due) AS "Due Date",

Tasks.agenda AS Person,

choice(project, project, Tasks.project) AS "Project",

("[[" + file.name + "|🔗]]") AS "Link"

  

FROM -"Knowledge Base" AND -"Templates"

FLATTEN file.tasks AS Tasks

WHERE !Tasks.completed AND !Tasks.delegated AND !Tasks.reporting AND Tasks.agenda AND Tasks.status != "D" AND Tasks.status != "-"

SORT Tasks.due ASC

```

# Reporting

```dataview

TABLE WITHOUT ID

regexreplace(regexreplace(Tasks.text, "\[(reporting|project)::.*\]", ""), "📅.*", "") AS Task,

choice(Tasks.due, choice(Tasks.due < striptime(date(now)), "⚠️ " + dateformat(Tasks.due, "dd MMM yy") ,dateformat(Tasks.due, "dd MMM yy")), Tasks.due) AS "Due Date",

Tasks.reporting AS Person,

choice(project, project, Tasks.project) AS "Project",

("[[" + file.name + "|🔗]]") AS "Link"

  

FROM -"Knowledge Base" AND -"Templates"

FLATTEN file.tasks AS Tasks

WHERE !Tasks.completed AND !Tasks.delegated AND !Tasks.agenda AND Tasks.reporting AND Tasks.status != "D" AND Tasks.status != "-"

SORT Tasks.due ASC

```




# Deferred Tasks

```dataview

TASK

FROM -"Knowledge Base"

WHERE !due and !completed and !delegated and !agenda and status = "D"

SORT priority

```