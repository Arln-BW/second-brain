___
```dataview
TABLE file.folder AS Path, file.etags AS "File Tags" FROM #daily and !"Templates"
sort file.name desc
```
