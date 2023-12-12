---
title : "Callout"
excerpt : "Callout"
toc : true
toc_sticky : true
toc_label : "Callout"
categories:
- Obsidian
tags:
- [Obsidian]
last_modified_at: 2023-11-15T08:00:00-10:00:00
---

# 날짜 : 2023-11-15 17:13

# 태그 : #Obsidian 
---

# 내용

## callout이란
>
>강조되는 추가 컨텐츠, 또는 컨텐츠 그룹화에 사용되는 syntax

## 사용법

### 제목 변경
- 식별자 뒤에 text를 추가하여 변경
```
> <제목명>
>내용

```

### 접기 펼치기
- 식별자 뒤에 더하기 또는 빼기를 추가
```
> [!faq]- Are callouts foldable?
> Yes! In a foldable callout, the contents are hidden when the callout is collapsed.

```

### 중첩
- 여러 수준을 중첩 할 수 있다
```
> Can callouts be nested? 
>> Yes!, they can. 
>>> You can even use multiple layers of nesting.

```

### custom callout
- css 스니펫 수정

```css
.callout[data-callout="custom-question-type"] { 
	--callout-color: <rgb 값으로 된 컬러>;
	--callout-icon: <lucide icon id>; 
	/*--callout-icon: '<svg>...custom svg...</svg>';*/
	}
```

### 지원 유형

#### 메모
```
> 
> Lorem ipsum dolor sit amet

```

#### 추상적인
```
> 
> Lorem ipsum dolor sit amet

```

#### 정보
```
> 
> Lorem ipsum dolor sit amet

```

#### 할것
```
> 
> Lorem ipsum dolor sit amet

```

#### 팁
```
> 
> Lorem ipsum dolor sit amet

```

#### 성공
```
> 
> Lorem ipsum dolor sit amet

```

#### 질문
```
>
> Lorem ipsum dolor sit amet

```

#### 경고
```
> 
> Lorem ipsum dolor sit amet

```

#### 실패
```
> 
> Lorem ipsum dolor sit amet

```

#### 위험
```
> 
> Lorem ipsum dolor sit amet

```

#### 버그
```
> 
> Lorem ipsum dolor sit amet

```

#### 예
```
> 
> Lorem ipsum dolor sit amet

```

#### 인용
```
> 
> Lorem ipsum dolor sit amet

```

---

# 연결문서
- lucide icons : https://lucide.dev/icons/categories?search=book#shapes