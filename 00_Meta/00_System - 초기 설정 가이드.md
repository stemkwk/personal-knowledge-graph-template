---
uid: 01K6T7CMFJE1EDF6Y81YEASZVT
tags:
  - type/rule
  - status/complete
  - category/meta
created: 2025-10-04
publish: false
aliases:
  - "셋업 가이드"
  - "Getting Started"
  - "시스템 설정"
source:
  - medium: url
    value: "https://help.obsidian.md/"
    title: "Obsidian Help"
  - medium: url
    value: "https://git-scm.com/doc"
    title: "Git Documentation"
  - medium: url
    value: "https://docs.github.com/en/codespaces"
    title: "GitHub Codespaces Documentation"
description: "새로운 컴퓨터 환경에서 이 지식 그래프 시스템을 사용하기 위한 초기 설정 절차"
author: "admin"
---

# 초기 설정 가이드

> **한 줄 정의**: 새로운 컴퓨터 환경에서 이 지식 그래프 시스템을 사용하기 위한 초기 설정 절차.

이 문서는 원격(브라우저) 환경과 로컬(개인 PC) 환경에서의 설정 방법을 각각 안내한다.

## 1. 원격 환경 설정 (GitHub Codespaces)

인터넷 브라우저만 있으면 어디서든 노트를 '기록'할 수 있는 환경을 설정한다.

## 1. 원격 환경 설정 (GitHub Codespaces)

인터넷 브라우저만 있으면 어디서든 노트를 '기록'할 수 있는 환경을 설정한다.

### 1.1. Codespace 생성
1.  이 저장소의 GitHub 페이지로 이동한다.
2.  오른쪽 상단의 녹색 **`< > Code`** 버튼을 클릭한다.
3.  **`Codespaces`** 탭을 선택한다.
4.  **`Create codespace on main`** 버튼을 클릭한다. (최초 생성 시 1~2분 소요될 수 있다.)

## 2. 로컬 환경 설정 (Obsidian)

개인 PC에서 지식을 '연결'하고 '재학습'하기 위한 환경을 설정한다.

### 2.1. 필수 프로그램 설치
1.  **Git**: [git-scm.com/downloads](https://git-scm.com/downloads) 에서 자신의 운영체제에 맞는 Git을 설치한다.
2.  **Obsidian**: [obsidian.md](https://obsidian.md/) 에서 Obsidian을 설치한다.

### 2.2. 저장소 복제 (Clone)
1.  이 저장소의 GitHub 페이지로 이동하여 **`< > Code`** 버튼을 누른 뒤, HTTPS 주소를 복사한다.
2.  PC에서 터미널(Windows는 Git Bash, Mac은 Terminal)을 연다.
3.  노트 보관소로 사용할 위치로 이동한다. (예: `cd Documents`)
4.  `git clone [붙여넣은 URL]` 명령어를 실행하여 저장소 전체를 컴퓨터로 내려받는다.

### 2.3. Obsidian Vault 열기
1.  Obsidian 프로그램을 실행한다.
2.  `Open folder as vault` 버튼을 클릭한다.
3.  방금 전 `git clone` 명령어로 생성된 폴더(예: `personal-knowledge-graph`)를 선택하여 Vault로 연다.

### 2.4. Obsidian 핵심 설정
1.  Obsidian 왼쪽 하단의 **설정(톱니바퀴 모양)** 아이콘을 클릭한다.
2.  `파일 및 링크` 탭으로 이동한다.
3.  **`새 첨부 파일을 만들 기본 위치`** 설정을 찾는다.
4.  드롭다운 메뉴에서 **`아래에 지정된 폴더에`**를 선택한다.
5.  바로 아래 나타나는 텍스트 상자에 **`_Assets`** 라고 입력한다. 이 설정은 모든 이미지/PDF 파일이 해당 폴더에 깔끔하게 정리되도록 보장한다.

---
## 맥락

- `[[01_Protocol - PKG 노트 작성 규칙.md]]`