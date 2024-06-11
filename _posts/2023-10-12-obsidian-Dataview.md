---
title : "Dataview"
excerpt : "Dataview"
toc : true
toc_sticky : true
toc_label : "Dataview"
categories:
- Obsidian
tags:
- [Obsidian]
last_modified_at: 2023-10-12T08:00:00-10:00:00
---
  
---
  
## 결과 타입
- TABLE : 표 형식으로 Annotaion에 따라 어떤 컬럼을 보여줄지 설정
  
```sql
TABLE time-played, length, rating 
FROM "games" 
SORT rating desc
```  
- LIST : from 에 해당하는 모든 노트를 가져옴
  
```sql
LIST FROM #game/moba or #game/crpg
```  
- TASK : from 에 해당하는 모든 노트의 task를 가져옴
  
```sql
TASK FROM #projects/active
```
  
## Annotation
- 어떤 데이터를 Dataview에 가져오는 표기방법
  
### 프론트메터
- 노트 맨 앞에 작성하는 메타데이터

```  
--- 
created: 2021-11-12 
wakeup: 07:00 
sleep: 23:30 
workout: ✅ 
gratitude: ✅ 
---
```

```
TABLE wakeup as 기상시간, sleep as 취침시간, workout as 운동, gratitude as 감사일기 FROM 2021-11-12
```
  
### 인라인 필드
- 노트 중간에 작성하는 필드
- 작성법 : \[drama:: 오징어게임\], \[DP\]

```
TABLE drama as 드라마 FROM "/" WHERE file.name = "드라마"
```
  
### 자체 내장
- 옵시디언에서 제공해주는 필드
  
#### 자체내장 필드 리스트
- this : 현재 개체
- file : 노트 자체
- file.name:  파일명  
- file.folder: 해당 파일이 속한 폴더명  
- file.path: 해당 파일이 속한 전체 경로  
- file.link: 해당 파일의 링크  
- file.size: 해당 파일의 크기  
- file.ctime: 해당 파일이 만들어진 시간(시간 + 날짜)  
- file.cday: 해당 파일이 만들어진 날짜  
- file.mtime: 해당 파일이 수정된 시간(시간 + 날짜)  
- file.mday: 해당 파일이 수정된 날짜  
- file.tags: 해당 파일에 존재하는 모든 태그에 대한 배열   
- file.inlinks: 해당 파일을 참조하는 다른 노트들 목록  
- file.outlinks: 해당 파일이 참조하는 다른 노트들 목록
- file.tasks: 해당 파일에 존재하는 모든 할일목록(체크리스트)
- file.aliases: 해당 노트의 alias
  
## from 절
- 태그 : \#{태그명}
- 폴더 경로 : /{폴더명}
- 인링크 : {노트명}
- 아웃링크 : outgoing{노트명}
  
## 기타함수
- choice(<조건절>, <참일때 값>, <거짓일때 값>) : 조건문 
{: .notice}  
  
```sql
choice(contains(file.tags, "#미완료"), "🚫", "⏩") as 진행상태
```  
- contains(<리스트>, <값>) : 포함여부 확인 
{: .notice}  
  
```sql
choice(contains(file.tags, "#미완료"), "🚫", "⏩") as 진행상태
```  
- filter(<리스트>, <필터링 함수>) : 리스트 필터링 
{: .notice}  
  
```sql
filter(file.tasks, (x) => !x.completed) 
{: .notice}  
```  
- map(<리스트>, <선택 함수>) : 요소 속성중 원하는 속성만 선택 
{: .notice}  
  
```sql
map(filter(file.tasks, (x) => !x.completed), (x) => x.text) 
{: .notice}  
```

---
  
# 연결문서
- 참고사이트 : https://blacksmithgu.github.io/obsidian-dataview/reference/functions/
  
