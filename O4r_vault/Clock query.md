
```dataview
table task.text as "Task", task.clock as "Clock", task.header as "Header", task.tags as "Task type"
from "Daily Notes"
flatten file.tasks as task
where task.clock

```

