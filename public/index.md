
```dataviewjs

const folderPath = app.workspace.getActiveFile().parent.path;
const pages = dv.pages(`"${public}"`).where(p => p.tags && p.file.path.startsWith(public));

const tagMap = new Map();

for (const page of pages) {
    const tags = Array.isArray(page.tags) ? page.tags : [page.tags];
    for (const tag of tags) {
        if (!tagMap.has(tag)) tagMap.set(tag, []);
        tagMap.get(tag).push(page);
    }
}

for (const [tag, entries] of tagMap.entries()) {
    const tagId = tag.replace(/[^a-zA-Z0-9]/g, "_");
    dv.el("details", null, { open: false }).appendChild(
        createTagSection(tag, entries, tagId)
    );
}

function createTagSection(tag, entries, tagId) {
    const section = document.createElement("div");
    const summary = document.createElement("summary");
    summary.innerText = `${tag} (${entries.length})`;
    section.appendChild(summary);

    const table = dv.table(
        ["File", "Created", "Tags"],
        entries.map(p => [
            dv.fileLink(p.file.path),
            p.file.ctime.toLocaleDateString(),
            Array.isArray(p.tags) ? p.tags.join(", ") : p.tags
        ])
    );

    section.appendChild(table);
    return section;
}


```
