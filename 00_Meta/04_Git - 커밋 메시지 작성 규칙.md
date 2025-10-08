---
uid: 01K6T7EMXFX1361GQEDCQ3D7GM
tags:
  - type/rule
  - status/complete
  - category/meta
created: 2025-10-04
publish: false
aliases:
  - "커밋 컨벤션"
  - "Git Commit Convention"
source:
  - medium: internal
  - value: "[[01_Protocol - PKG 노트 작성 규칙.md]]"
description: "Git을 통해 수정 이력을 의미 있는 방식으로 기록하기 위한 커밋 메시지 작성 규칙."
---

# 커밋 메시지 규칙

> **한 줄 정의**: Git을 통해 수정 이력을 의미 있는 방식으로 기록하기 위한 커밋 메시지 작성 규칙.

## 구조

`타입: 제목`

- **타입**: 변경의 목적을 나타내는 키워드
- **제목**: 변경 내용에 대한 간결한 설명

## 1. 타입(Type) 목록

| 타입 | 설명 (언제 사용하는가) |
| :--- | :--- |
| **`feat`** | **새로운 노트(Create)**를 추가했을 때 |
| **`refine`** | **기존 노트의 내용을 보강(Update)**했을 때 |
| **`fix`** | **오타나 사실 관계 오류를 수정(Update)**했을 때 |
| **`link`** | **MOC를 업데이트하거나 링크를 주로 수정**했을 때 |
| **`refactor`** | **파일을 이동하거나 이름을 변경**했을 때 |
| **`docs`** | **설명서(README, 규칙, 가이드라인)의 내용을 수정**했을 때 |
| **`chore`** | **템플릿이나 시스템 설정 등 '도구'를 수정**했을 때 |
| **`delete`** | **노트를 삭제(Delete)**했을 때 |

## 2. 예시(Example)

- `feat: '중력의 본질'에 대한 질문 노트 추가`
- `refine: '일반 상대성 이론' 노트 내용 보강`
- `fix: '양자역학' 노트의 수식 오류 수정`
- `link: 수학 MOC에 '미적분학' 개념 연결`
- `refactor: '열역학 제1법칙' 파일명을 '에너지 보존 법칙'으로 변경`
- `docs: README 파일 폴더 구조 설명 업데이트`
- `chore: 기본 노트 템플릿에 'publish' 속성 추가`
- `delete: 중복된 '중력' 관련 질문 노트 삭제`

---
## 맥락

- `[[01_Protocol - PKG 노트 작성 규칙.md]]`