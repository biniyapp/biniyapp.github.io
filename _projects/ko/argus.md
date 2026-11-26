---
title: "Argus (공공의 적) - npm 공급망 악성코드 탐지 레지스트리 프록시"
summary: "화이트햇스쿨 팀 프로젝트. npm 패키지 설치 요청을 가로채 악성 여부를 검사하고 허용·차단을 결정하는 레지스트리 프록시를 구축"
type: team
team_size: "8명"
role: "PM · Scanner"
period: "2026.08 ~ TODO: 종료 시점"
tags: ["npm", "공급망 보안", "정적·동적 분석", "PM"]
cat: malware
order: 1
---

## 개요
오픈소스 공급망 공격에 대응하기 위해, 조직이 `npm install` 할 때 패키지를 사전에 검사하는 **레지스트리 프록시**를 만든 프로젝트입니다. 기업 보안 담당자 관점에서 예방과 탐지에 초점을 맞췄고, 대상은 npm 생태계로 한정했습니다.

- 흐름: `npm install` → Gateway / Verdaccio → 패키지 검사 → ALLOW / REVIEW / DENY → Dashboard에서 확인
- 최종 스택: Verdaccio, Fastify Gateway, GuardDog(1차 정적 분석), Fakeium(경량 JS 동적 샌드박스), Redis/BullMQ, NestJS/PostgreSQL, React/Vite 대시보드

## 내 역할 요약
**PM**과 **Scanner**를 함께 맡았습니다.
- **PM**: 8명 팀의 일정, 역할 분담, 협업 체계, 멘토 피드백 반영을 총괄
- **Scanner**: 패키지 탐지 로직과 분석을 담당하고, 1차(Tier1) / 2차(Tier2) 검사 구현에 참여

## 전체 구조
TODO: 아키텍처 그림 1장 (Gateway → Verdaccio → Scanner → Dashboard) 과 Scanner의 위치 설명

## Scanner 상세
> 상세 내용은 직접 작성 예정

### 구성
- 1차: GuardDog 기반 정적 분석
- 2차: 정적 분석 결과를 동적으로 검증하는 구조. 정적 Finding마다 CONFIRMED / NOT_OBSERVED / REFUTED로 판정하는 "정적 가설 검증기"로 설계
- 동적 분석은 Fakeium(V8 isolate에서 JS API 호출 로깅)을 먼저 적용하고, 컨테이너 기반 실제 실행 Runner는 이후 확장으로 계획

### 내가 구현한 부분
TODO: 본인이 직접 구현·분석한 항목을 구체적으로 (예: 탐지 로직, 룰, 파이프라인 연동)

### 막혔던 점과 해결
TODO: 오탐/미탐 사례, 해결 과정

## PM 활동
- **킥오프와 운영**: 킥오프 후 주 2회 정기 회의와 주 1회 멘토링 체계를 운영
- **역할 설계**: 팀원 경험 수준을 고려해 Gateway, Registry, Scanner, Data 등 트랙을 나누고, 팀원 피드백을 반영해 조직 구조를 조정
- **스코프 관리**: 약 2개월 반의 기간에 맞춰 Verdaccio 프록시 + GuardDog 탐지 엔진 + 자체 대시보드로 완성물을 한정하고, 자체 레지스트리·멀티 생태계·GNN 탐지는 범위에서 제외
- **일정 계획**: 8월 MVP 완성을 1차 목표로 하고, 9월에 동적 분석과 AI 탐지를 단계적으로 추가
- **협업 규칙**: main / develop / feature 브랜치 전략, Issue → PR → 코드 리뷰 → 병합 흐름, 커밋 컨벤션 정립
- **멘토 피드백 반영**: 설계 전에 threat modeling과 workflow를 먼저 정의하라는 피드백을 받아 설계 순서를 조정
- **프로토타입**: 조사 단계에서 Verdaccio + 프록시 + GuardDog 연동 구조를 직접 구현해, 설치 요청을 가로채 검사 후 허용하거나 403으로 차단하는 흐름을 검증

TODO: 회의록·일정표 등 근거 자료 링크

## 성과
TODO: 산출물, 수치, GitHub 링크

## 배운 점
TODO: 한두 줄 (PM 경험과 Scanner 개발 관점에서)
