---
created: <% tp.file.creation_date("YY-MM-DD") %>
---
tags:: [[Daily Notes]]

# <% moment(tp.file.title,'YYYY-MM-DD').format("dddd, MMMM DD, YYYY") %>

---
## 📋 Today's Tasks

```tasks
not done
due <% moment(tp.file.title, 'YYYY-MM-DD') %>
sort by priority, due
```
### ❗️Overdue Tasks

```tasks
not done
due before <% moment(tp.file.title, 'YYYY-MM-DD') %>
sort by priority, due
```

### ✅ Other tasks completed today

```tasks
done <% moment(tp.file.title, 'YYYY-MM-DD') %>
path does not include {{query.file.path}}
```
---
## 📝 Journal

- 

---
### Today's meetings

```dataview

List FROM "Journal/Meetings"  
WHERE date = "<% moment(tp.file.title,'YYYY-MM-DD').format("YY-MM-DD") %>"

SORT date asc
```

### Notes created today

```dataview
List FROM "" WHERE file.cday = date("<% moment(tp.file.title,'YYYY-MM-DD').format("YYYY-MM-DD") %>") SORT file.ctime asc
```

### Notes last touched today

```dataview
List FROM "" WHERE file.mday = date("<%moment(tp.file.title,'YYYY-MM-DD').format("YYYY-MM-DD")%>") SORT file.mtime asc
```