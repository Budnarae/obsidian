
```dataviewjs
const folder = app.workspace.getActiveFile().parent.path;
const pages = dv.pages().where(p => p.file.path.startsWith(folder) && p.file.tags);

const tagMap = new Map();

for (let page of pages) {
    let tags = Array.isArray(page.file.tags) ? page.file.tags : [page.file.tags];
    for (let tag of tags) {
        if (!tagMap.has(tag)) tagMap.set(tag, []);
        tagMap.get(tag).push(page);
    }
}

// 각 태그에 대해 details 요소를 Dataview 방식으로 만들기
for (let [tag, entries] of tagMap) {
    // details 및 summary 생성
    const container = dv.el("details", "", { open: false });
    const summary = document.createElement("summary");
    summary.innerText = `${tag} (${entries.length})`;
    container.appendChild(summary);

    // Dataview 테이블 생성 → DOM이 아님 → 따로 render
    dv.container.appendChild(container);
    
    dv.table(
        ["File", "Created", "Tags"],
        entries.map(p => [
            dv.fileLink(p.file.path),
            new Date(p.file.ctime).toLocaleDateString(),
            Array.isArray(p.file.tags) ? p.file.tags.join(", ") : p.file.tags
        ]),
        container // 이 table은 여기 container 안에 그려짐
    );
}
```
