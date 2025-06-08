---
created: <% tp.file.creation_date() %>
tags: type/daily_note 
---
# <% moment(tp.file.title,'YYYY-MM-DD').format("dddd") %>, <% moment(tp.file.title,'YYYY-MM-DD').format("DD") %> [[<% moment(tp.file.title,'YYYY-MM-DD').format("MM-MMMM YYYY") %>|<% moment(tp.file.title,'YYYY-MM-DD').format("MMMM") %>]] <% moment(tp.file.title,'YYYY-MM-DD').format("YYYY") %>

## Day planner

<%*
if (tp.date.now("dddd", 0, tp.file.title, "YYYY-MM-DD") === "Monday") { -%>
  - 10:00 - 13:00 [[Project A]]
	```tasks
		not done
		tags include #planner/morning
		hide tags
		hide task count
		hide backlink
		show tree 
	```
  - 13:00 - 14:00 Lunch
  - 14:00 - 19:00 [[Project A]]
	```tasks
		not done
		tags include #planner/afternoon
		hide tags
		hide task count
		hide backlink
		show tree 
	```
<%* } else if (tp.date.now("dddd", 0, tp.file.title, "YYYY-MM-DD") === "Tuesday") { -%> 
  - 10:00 - 13:00 [[Project A]]
	```tasks
		not done
		tags include #planner/morning
		hide tags
		hide task count
		hide backlink
		show tree 
	```
  - 13:00 - 14:00 Lunch
  - 14:00 - 19:00 [[Project A]]
	```tasks
		not done
		tags include #planner/afternoon
		hide tags
		hide task count
		hide backlink
		show tree 
	```
<%* } else if (tp.date.now("dddd", 0, tp.file.title, "YYYY-MM-DD") === "Wednesday") { -%> 
  - 10:00 - 13:00 [[Project A]]
	```tasks
		not done
		tags include #planner/morning
		hide tags
		hide task count
		hide backlink
		show tree 
	```
  - 13:00 - 14:00 Lunch
  - 16:00 - 19:00 [[Project A]]
<%* } else if (tp.date.now("dddd", 0, tp.file.title, "YYYY-MM-DD") === "Thursday") { -%> 
  - 10:00 - 13:00 [[Project B]]
	```tasks
		not done
		tags include #planner/morning
		hide tags
		hide task count
		hide backlink
		show tree 
	```
  - 13:00 - 14:00 Lunch
  - 14:00 - 19:00 [[Project B]]
	```tasks
		not done
		tags include #planner/afternoon
		hide tags
		hide task count
		hide backlink
		show tree 
	```
<%* } else if (tp.date.now("dddd", 0, tp.file.title, "YYYY-MM-DD") === "Friday") { -%> 
  - 10:00 - 13:00 [[Project B]]
	```tasks
		not done
		tags include #planner/morning
		hide tags
		hide task count
		hide backlink
		show tree 
	```
  - 13:00 - 14:00 Lunch
  - 14:00 - 19:00 [[Project B]]
	```tasks
		not done
		tags include #planner/afternoon
		hide tags
		hide task count
		hide backlink
		show tree 
	```
<%* }
-%>

----------------
## To do ✅
```tasks
not done
group by heading
show tree
hide postpone button
hide edit button
```




----------------
## Today's notes 📃






