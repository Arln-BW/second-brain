## Projects

### By Deadline

```dataview
TABLE Status, Deadline, Area
from #project AND !"Templates"
sort Deadline asc
```

### Not Started
```dataview
table Status, Deadline
from [[]] AND #project 
where contains(Status, "🟥")
```

### In Progress
```dataview
table Status, Deadline
from [[]] AND #project 
where contains(Status, "🟨")
```

