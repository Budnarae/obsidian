
```dataviewjs

// 1. 설정: 제외할 태그 목록 (필요에 따라 수정)
const excludeTags = [
    "#제외할태그", "#제외할태그/", // 예시: 특정 태그와 그 하위 태그
    "#개인정보", "#개인정보/",   // 예시: 또 다른 제외 태그
    "#Template", "#Template/",  // 템플릿 관련 태그
    "#Excalidraw", "#Excalidraw/" // Excalidraw 관련 태그
];

// 2. 파일 가져오기 (현재 폴더 및 하위 폴더)
const currentFolderPath = dv.current().file.folder;
const files = dv.pages(`"${currentFolderPath}"`)
              .where(p => p.file.tags && p.file.tags.length > 0) // 태그가 있는 파일만
              .filter(p => !p.file.name.includes("Template") && !p.file.name.includes("Excalidraw")); // 템플릿/Excalidraw 파일명 제외

// 3. 태그별로 파일 그룹화
const taggedNotes = new Map();

for (const file of files) {
    for (const tag of file.file.tags) {
        // 제외할 태그 필터링
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

// 5. HTML 출력 생성 (접기/펴기 기능 및 개선된 링크 포함)
let output = '';

// 각 태그 그룹을 접기/펴기 가능한 섹션으로
for (const tag of sortedTags) {
    const notesInTag = taggedNotes.get(tag).sort((a, b) => a.file.name.localeCompare(b.file.name));
    
    output += `<details class="dataview-tag-group">`; // 커스텀 클래스 추가
    output += `<summary><strong><span class="math-inline">\{tag\}</strong\> <span class\="note\-count"\>\(</span>{notesInTag.length}개)</span></summary>`;
    output += `<ul class="dataview-note-list">`; // 커스텀 클래스 추가

    for (const note of notesInTag) {
        // dv.markdownLink 대신 직접 Markdown 링크 문자열 생성
        // file.path는 'folder/filename.md' 형태, file.name은 'filename'
        const noteLink =

```