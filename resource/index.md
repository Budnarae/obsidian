
```dataviewjs

const pages = dv.pages('"."')
  .where(p => p.file.path.includes(dv.current().file.folder));

const tagsMap = new Map();

for (let page of pages) {
  if (!page.tags) continue;

  const tags = Array.isArray(page.tags) ? page.tags : [page.tags];
  
  for (let tag of tags) {
    if (!tagsMap.has(tag)) {
      tagsMap.set(tag, []);
    }
    tagsMap.get(tag).push(page);
  }
}

for (let [tag, group] of tagsMap.entries()) {
  dv.header(3, tag);
  dv.list(group.map(p => p.file.link));
}

```