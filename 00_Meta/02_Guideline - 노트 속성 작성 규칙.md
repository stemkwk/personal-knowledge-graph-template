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
  - "[[01_Protocol - PKG 노트 작성 규칙.md]]"
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
- **목적**: 정보의 출처를 명시하여 신뢰성을 높이고, 추후 참조를 용이하게 한다.
- **규칙**: 하이픈(`-`)을 사용하여 목록(List) 형식으로 기입한다.
    - **내부 문서**: 따옴표로 감싼 `"[[파일 링크]]"` 형식으로 연결한다.
    - **외부 정보**: URL이나 책 제목 등 텍스트를 `"[설명](url)"` 형식으로 따옴표로 감싸 기입한다.

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
  - "https://ko.wikipedia.org/wiki/슈뢰딩거의_고양이"
  - "Erwin Schrödinger, <Die gegenwärtige Situation in der Quantenmechanik>"
description: "양자 중첩 상태가 거시 세계의 대상에 어떻게 적용되는지의 역설을 보여주는 사고 실험."
author: "schrdg-cat"
image: "[[_Assets/images/schrodingers-cat.png]]"
```

---
## 맥락

- `[[01_Protocol - PKG 노트 작성 규칙.md]]`