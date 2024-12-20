---
date: <% tp.file.creation_date("YY-MM-DD") %>
location: 
type: meeting
companies: 
topics: 
project: 
attendees: 
summary:
---
tags: [[Meetings]]
<% await tp.file.move("/Journal/Meetings/" + tp.date.now("YYYY") + "/" + tp.date.now("MM-MMMM") + "/" + tp.date.now("DD-dddd") + "/" + tp.file.title) %>
# <% tp.date.now("DD. MMMM YY") + " - " + tp.file.title %>

👩‍💼👨‍💼 **Other Attendees**: 
- 

## Agenda/Questions

- 

## Notes

- 

## Next Steps

- 