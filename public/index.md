
```dataview

TABLE WITHOUT ID
  tag AS "태그",
  length(rows.file.link) AS "문서 수",
  rows.file.link AS "문서 목록"
FROM "public"
WHERE file.tags 
  AND !contains(file.name, "Template") 
  AND !contains(file.name, "Excalidraw")
FLATTEN file.tags AS tag
WHERE !startswith(tag, "#참고링크/")  AND tag != "#참고링크"
  AND !startswith(tag, "#참고도서/") AND tag != "#참고도서"
GROUP BY tag
SORT tag ASC

```