---
uid: 01K6T7D3V1R0HT9NG9H0B69QKS
tags:
  - type/rule
  - status/complete
  - category/meta
created: 2025-10-03
publish: false
aliases:
  - "노트 속성 컨벤션"
  - "YAML 규칙"
  - "Frontmatter Rules"
source:
  - medium: internal
    value: "[[01_Protocol - PKG 노트 작성 규칙.md]]"
description: "모든 노트 최상단의 YAML Frontmatter(속성) 영역에 일관된 메타데이터를 작성하기 위한 규칙."
author: "admin"
---

# 노트 속성 작성 규칙

> **한 줄 정의**: 모든 노트 최상단의 YAML Frontmatter(속성) 영역에 일관된 메타데이터를 작성하기 위한 규칙.

이 규칙은 노트의 검색 가능성과 데이터의 독립성을 보장하는 것을 목표로 한다.

## 1. 필수 속성 (Required Properties)

모든 노트에 **반드시 포함되어야 하는** 핵심 속성이다.

### 1.1. `uid` (Unique Identifier)
- **목적**: 파일 이름이 변경되더라도 노트의 고유성을 보장하는 영구 식별자. 외부 애플리케이션 연동 시 데이터 무결성을 위해 필수적이다.
- **규칙**: 노트 생성 시 **ULID(Universally Unique Lexicographically Sortable Identifier)**를 부여하며, 이 값은 한번 부여된 후 절대 수정하지 않는다. (플러그인이나 확장 프로그램을 통해 자동으로 생성한다.)

### 1.2. `tags`
- **목적**: 노트의 종류, 상태, 분야를 정의하여 분류 및 필터링을 용이하게 한다.
- **규칙**: `type/`, `status/`, `category/` 의 계층 구조를 사용한다.
    - **`type/`**: `rule`, `map`, `question`, `concept`, `idea/proposal`, `idea/hypothesis` 중 택일
    - **`status/`**: `draft`, `progress`, `complete` 중 택일
    - **`category/`**: `meta`, `math`, `science`, `computer` 등 확장 가능한 학문 분야

### 1.3. `created`
- **목적**: 노트 내 아이디어가 발생한 의미론적 날짜를 기록하여 시간적 맥락을 부여한다.
- **규칙**: `YYYY-MM-DD` 형식으로 작성한다.

### 1.4. `publish`
- **목적**: 노트의 외부 공개 여부를 명시적으로 결정한다. 모든 노트는 공개 또는 비공개 상태를 반드시 가져야 한다.
- **규칙**: `true` 또는 `false` 값을 사용한다.

## 2. 권장 속성 (Recommended Properties)

필수는 아니지만, 지식의 맥락을 풍부하게 하고 애플리케이션 활용도를 높이기 위해 **적극적으로 사용하는 것을 권장하는** 속성이다.

### 2.1. `aliases`
- **목적**: 노트의 다른 이름(별칭, 축약어, 영문명 등)을 지정하여 링크의 유연성을 확보한다.
- **규칙**: 하이픈(`-`)을 사용하여 목록(List) 형식으로 기입하며 따옴표로 감싸 기입한다.

### 2.2. `source`

* **목적**: 정보의 출처를 명시하여 신뢰성을 높이고, **출처의 종류를 식별하고 데이터를 활용**할 수 있도록 합니다.
* **규칙**: 하이픈(`-`)을 사용하여 **객체(Object)의 목록(List)** 형식으로 기입합니다.
    * 모든 출처 객체는 **`medium` 키를 반드시 포함**해야 합니다.
    * 각 `medium`에 따라 권장되는 추가 키를 사용하여 출처 정보를 상세하고 일관되게 기록합니다.

### 2.2.1. `source` 타입 목록

#### 1. **`internal`**: 다른 노트

* **설명**: 지식 그래프 내의 다른 노트를 출처로 삼을 때 사용합니다.
* **필수 키**: `value` (Obsidian 링크 형식)
* **예시**:
```yaml
source:
  - medium: internal
    value: "[[01_Protocol - PKG 노트 작성 규칙.md]]"
```
#### 2. **`url`**: 웹사이트, 기사

* **설명**: 온라인 기사, 블로그 포스트, 웹사이트 등 일반적인 웹 출처에 사용합니다.
* **필수 키**: `value`, `title`
* **권장 키**: `author`, `access_date`
* **예시**:
```yaml
source:
  - medium: url
    value: "[https://ko.wikipedia.org/wiki/](https://ko.wikipedia.org/wiki/)..."
    title: "위키피디아: 개인 지식 관리"
    author: "Wikipedia Contributors"
    access_date: "2025-10-08"
```

#### 3. **`book`**: 책

* **설명**: 단행본, 교재 등 서적을 출처로 사용할 때 사용합니다.
* **필수 키**: `title`, `author`, `isbn`
* **권장 키**: `publisher`, `year`
* **예시**:
```yaml
source:
  - medium: book
    title: "Thinking, Fast and Slow"
    author: "Daniel Kahneman"
    isbn: "978-0374275631"
    publisher: "Farrar, Straus and Giroux"
    year: 2011
```

#### 4. **`paper`**: 논문

* **설명**: 학술지, 학회 등에 발표된 논문을 출처로 사용할 때 사용합니다.
* **필수 키**: `title`, `author`, `doi`
* **권장 키**: `journal`, `year`
* **예시**:
```yaml
source:
  - medium: paper
    title: "Attention Is All You Need"
    author: "Ashish Vaswani, et al."
    doi: "10.48550/arXiv.1706.03762"
    journal: "NIPS"
    year: 2017
```

#### 5. **`person`**: 사람

* **설명**: 대화, 이메일, 강연 등 특정 인물로부터 직접 얻은 정보를 출처로 사용할 때 사용합니다.
* **필수 키**: `name`, `context`
* **권장 키**: `date`
* **예시**:
```yaml
source:
  - medium: person
    name: "John Doe"
    context: "Personal conversation about system architecture"
    date: "2025-10-07"
```

#### 6. **`recording`**: 영상, 팟캐스트

* **설명**: 유튜브 영상, 다큐멘터리, 팟캐스트 등 시청각 자료를 출처로 사용할 때 사용합니다.
* **필수 키**: `title`, `creator`
* **권장 키**: `platform`, `url`
* **예시**:
```yaml
source:
  - medium: recording
    title: "The Power of Habit"
    creator: "AsapSCIENCE"
    platform: "YouTube"
    url: "[https://www.youtube.com/watch?v=](https://www.youtube.com/watch?v=)..."
```

#### 7. **`event`**: 컨퍼런스, 강의

* **설명**: 컨퍼런스 발표, 세미나 등 특정 이벤트를 출처로 사용할 때 사용합니다.
* **필수 키**: `name`
* **권장 키**: `speaker`, `date`, `location`
* **예시**:
```yaml
source:
  - medium: event
    name: "Google I/O 2025 Keynote"
    speaker: "Sundar Pichai"
    date: "2025-05-12"
    location: "Online"
```

### 2.3. `description`
- **목적**: 외부 애플리케이션에서 노트 목록을 표시할 때 사용할 '미리보기'용 요약문을 제공한다.
- **규칙**: 노트 상단의 '한 줄 정의' 내용을 그대로 사용하며 따옴표로 감싸 기입한다.

## 3. 선택적 속성 (Optional Properties)

협업이나 특정 기능 구현 등 **필요한 경우에만 제한적으로 사용**하는 속성이다.

### 3.1. `author`
- **목적**: 협업 환경에서 노트의 '최초 작성자'를 Git 이력 분석 없이 빠르게 식별하기 위해 사용한다.
- **규칙**: GitHub 사용자 이름이나 식별 가능한 이름을 따옴표로 감싸 텍스트로 기입한다.

### 3.2. `image`
- **목적**: 노트를 대표하는 이미지를 지정한다. 주로 블로그 게시 등의 **대표 이미지나 썸네일로 활용**된다.
- **규칙**: `_Assets` 폴더에 있는 이미지 파일의 링크를 기입한다.

## 4. 사용하지 않는 속성 (Excluded Properties)

노트에 포함되어서는 안 되는 속성이다.

### 4.1. `updated`/`modified`
- **이유**: 모든 파일의 수정 이력은 Git 커밋 기록을 통해 자동으로 관리되므로, 중복 기록과 수동 관리의 부담을 줄이기 위해 사용하지 않는다.

## 5. 최종 예시 (Example)

```yaml
---
uid: 01K6QQG2RF3XWGS9TGM4RRZ7K0
tags:
  - type/concept
  - status/complete
  - category/science
created: 2025-10-04
publish: true
aliases:
  - "슈뢰딩거의 고양이"
  - "Schrodinger's Cat"
  - "고양이 역설"
source:
  - medium: url
    value: "https://ko.wikipedia.org/wiki/슈뢰딩거의_고양이"
    title: "슈뢰딩거의 고양이 - 위키백과, 우리 모두의 백과사전"
    access_date: "2025-10-08"
  - medium: paper
    title: "Die gegenwärtige Situation in der Quantenmechanik"
    author: "Erwin Schrödinger"
    doi: 10.1007/BF01491891
    journal: "Naturwissenschaften"
    year: 1935
description: "양자 중첩 상태가 거시 세계의 대상에 어떻게 적용되는지의 역설을 보여주는 사고 실험."
author: "schrdg-cat"
image: "[[_Assets/images/schrodingers-cat.png]]"
```

---
## 맥락

- `[[01_Protocol - PKG 노트 작성 규칙.md]]`