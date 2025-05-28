
```dataviewjs

// 1. 설정: 제외할 태그 목록 (필요에 따라 수정)
const excludeTags = [
    "#제외할태그", "#제외할태그/", 
    "#개인정보", "#개인정보/",   
    "#Template", "#Template/",  
    "#Excalidraw", "#Excalidraw/" 
];

// 2. 파일 가져오기 (현재 폴더 및 하위 폴더)
const currentFolderPath = dv.current().file.folder;
const files = dv.pages(`"${currentFolderPath}"`)
              .where(p => p.file.tags && p.file.tags.length > 0) 
              .filter(p => !p.file.name.includes("Template") && !p.file.name.includes("Excalidraw")); 

// 3. 태그별로 파일 그룹화
const taggedNotes = new Map();

for (const file of files) {
    for (const tag of file.file.tags) {
        let shouldExclude = false;
        for (const excludeTag of excludeTags) {
            if (tag === excludeTag || tag.startsWith(excludeTag + "/")) {
                shouldExclude = true;
                break;
            }
        }
        if (shouldExclude) {
            continue;
        }

        if (!taggedNotes.has(tag)) {
            taggedNotes.set(tag, []);
        }
        taggedNotes.get(tag).push(file);
    }
}

// 4. 태그를 알파벳 순으로 정렬
const sortedTags = Array.from(taggedNotes.keys()).sort();

// 5. HTML 출력 생성 (접기/펴기 기능 및 유효한 옵시디언 링크 포함)
let output = '';

for (const tag of sortedTags) {
    const notesInTag = taggedNotes.get(tag).sort((a, b) => a.file.name.localeCompare(b.file.name));
    
    output += `<details class="dataview-tag-group">`; 
    output += `<summary><strong>${tag}</strong> <span class="note-count">(${notesInTag.length}개)</span></summary>`;
    output += `<ul class="dataview-note-list">`; 

    for (const note of notesInTag) {
        // app.fileManager.generateMarkdownLink를 사용하여 유효한 옵시디언 링크 생성
        // note.file은 Obsidian의 TFile 객체 (or Dataview의 Simplified TFile)
        // note.file.path는 파일의 전체 경로 (예: "public/42 innercirle 정리.md")
        // note.file.name은 파일 이름 (예: "42 innercirle 정리")
        
        // 중요: generateMarkdownLink는 파일 객체를 직접 받거나, 경로와 별칭을 별도로 받습니다.
        // 여기서는 파일 객체(note.file)를 직접 전달하여 옵시디언이 정확한 링크를 생성하도록 합니다.
        // 두 번째 인자 'true'는 'display text'를 제공하는 경우 (여기서는 note.file.name)
        const obsidianInternalLink = app.fileManager.generateMarkdownLink(note.file, note.file.name);
        
        output += `<li>${obsidianInternalLink}</li>`;
    }

    output += `</ul>`;
    output += `</details>`;
}

// dv.el() 대신 dv.span() 또는 dv.paragraph()를 사용하여 Markdown 렌더링을 유도
// dv.el은 순수 HTML을 렌더링하고, dv.span/paragraph는 그 안의 Markdown을 다시 파싱합니다.
dv.el("div", output); // <div class="dataview-container"> 에 직접 HTML을 삽입
// dv.container.innerHTML = output; // 이 방법도 가능 (컨테이너에 직접 삽입)

// 만약 dv.el()이 여전히 링크를 렌더링하지 못한다면, Markdown을 강제 렌더링
// dv.paragraph(output); // 이 방법은 <p> 태그 안에 모든 HTML을 넣을 수 있음 (스타일 깨질 수 있음)
// dv.span(output); // 이 방법은 <span> 태그 안에 모든 HTML을 넣을 수 있음 (스타일 깨질 수 있음)

// 가장 좋은 방법은 DataviewJS가 HTML을 만들고, 그 HTML 안에 Markdown 링크가 있다면,
// 옵시디언 자체 렌더러가 다시 파싱해주기를 기대하는 것입니다.
// dv.el()은 기본적으로 HTML을 주입하므로, 그 안에 있는 [[...]]는 옵시디언이 후처리해야 합니다.
// 만약 안 된다면, Dataviewjs에서 마크다운을 렌더링하는 명시적인 방법인 dv.markdown()을 사용해볼 수 있습니다.
// 하지만 dv.markdown()은 전체 문자열을 마크다운으로 파싱하므로, HTML 구조를 유지하기 어렵습니다.

// 현재 코드에서 가장 유력한 해결책은 `app.fileManager.generateMarkdownLink`를 사용하는 것입니다.
// 이것이 안 된다면, Dataview와 Obsidian 버전 호환성에 문제가 있거나,
// 혹은 Obsidian의 다른 플러그인 충돌일 가능성이 있습니다.

```