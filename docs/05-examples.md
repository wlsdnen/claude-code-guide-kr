# 실전 CLAUDE.md 예시

[← 목차로 돌아가기](../README.md) · [이전: 안티패턴](04-anti-patterns.md)

---

바로 사용할 수 있는 CLAUDE.md 예시입니다. [`examples/`](../examples/) 디렉토리에서 파일을 복사하세요.

## 글로벌 CLAUDE.md (`~/.claude/CLAUDE.md`)

```markdown
# 개인 개발 선호도

## 핵심 원칙
- Clean Architecture 우선
- 가독성 > 복잡한 솔루션
- 변경 전 코드베이스 탐색, 복잡한 작업은 계획 후 구현
- 변경 후 테스트 실행

## 코딩 표준
- 모든 함수에 타입 힌트/타입 정의
- 작은 diff 선호 (요청하지 않은 리팩토링 금지)
- 로직 변경 시 테스트 필수
- 접근성: 레이블, 키보드 네비게이션

## 도구 선호도
- 패키지 매니저: bun (npm 대신)
- 린터: Biome (ESLint + Prettier 대체)
- 커밋: Conventional Commits
- 민감 데이터 커밋 금지

## 커뮤니케이션
- 아키텍처 결정 전 명확히 질문
- 비자명한 선택에 이유 문서화
- 코드 주석: 영어 / 문서: 한국어
```

## 프로젝트 CLAUDE.md (`./CLAUDE.md`)

```markdown
# E-Commerce Platform

## Overview
Next.js 14 기반 전자상거래 플랫폼. App Router 사용.

## Tech Stack
- Next.js 14 (App Router) + TypeScript (strict)
- Prisma + PostgreSQL, Tailwind CSS, Zod

## Architecture
- /app - Pages, layouts, API routes
- /components - 재사용 컴포넌트
- /lib - 유틸리티 및 DB 클라이언트
- /prisma - DB 스키마

## Commands
- npm run dev        # localhost:3000
- npm test           # Jest + RTL
- npm run db:push    # Prisma 스키마 푸시
- npm run lint       # ESLint + Prettier

## Conventions
- Server Components 기본, 인터랙션 필요 시만 'use client'
- DB 쿼리는 /lib/queries에 분리
- Zod 스키마로 모든 입력 검증

## Important
- 결제 코드는 /lib/payments 에서만 수정
- 환경 변수는 .env.example 참고
```

## 자기 개선 루프

CLAUDE.md를 살아있는 문서로 유지:

1. Claude가 실수하면 → 수정
2. 두 번째 동일 실수 → CLAUDE.md 업데이트
3. 2주마다 검토: 중복 제거, 구식 정보 갱신
4. PR 리뷰에서 잡힌 패턴 위반 → CLAUDE.md에 추가

---

[다음: 모듈화 →](06-modular-rules.md)
