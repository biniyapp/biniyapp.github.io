# biniyapp.github.io

Jekyll 기반 개인 포트폴리오 (한글/영문)

## 배포
1. GitHub에 `biniyapp.github.io` 이름의 public 레포 생성
2. 이 폴더 내용을 push (main 브랜치)
3. 레포 Settings > Pages > Source 를 `Deploy from a branch` / `main` / `/ (root)` 로 지정
4. 1~2분 뒤 https://biniyapp.github.io 접속

## 로컬 미리보기 (선택)
```
bundle install
bundle exec jekyll serve
# http://localhost:4000
```

## 프로젝트 추가 방법
`_projects/ko/` 와 `_projects/en/` 에 같은 파일명으로 .md 를 하나씩 추가
(파일명이 같아야 상단 언어 전환 버튼이 서로 연결됨). `order` 값으로 표시 순서 조정.

## 채워야 할 곳 (TODO 검색)
- `_config.yml`: 영문 이름, 이메일, 블로그 주소
- `_data/history.yml`: 기간
- `_data/skills.yml`: 기술 스택
- `_projects/*`: 각 프로젝트 본문
