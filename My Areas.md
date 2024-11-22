### Math
```dataview
list
from #area and !"Template" and #math
sort file.name asc
```
### Physics

```dataview
list
from #area and !"Template" and #physics
sort file.name asc
```

### HTML

```dataview
list
from #area and !"Template" and #html
sort file.name asc
```

### CSS

```dataview
list
from #area and !"Template" and #css
sort file.name asc
```

### JavaScript

```dataview
list
from #area and !"Template" and #js
sort file.name asc
```

## Belum Selesai
```dataview
TASK
FROM "6. Tasks"
GROUP BY file.name
SORT rows.file.ctime DESC
WHERE !completed
```
## Udah Selesai
```dataview
TASK
FROM "6. Tasks"
GROUP BY file.name
SORT rows.file.ctime DESC
WHERE completed
```
