
```dataview

TABLE WITHOUT ID
  tag AS "TAG",
  LENGTH(rows.file.link) AS "NOTES NUMBER",
  FLATTEN(rows.file.link) AS "NOTES LIST"
FROM ""
WHERE file.tags AND !contains(file.name, "Template") AND !contains(file.name, "Excalidraw")
FLATTEN file.tags AS tag
GROUP BY tag
SORT tag ASC

```