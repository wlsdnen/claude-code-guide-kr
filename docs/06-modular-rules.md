# 모듈화 (.claude/rules/)

[← 목차로 돌아가기](../README.md) · [이전: 실전 예시](05-examples.md)

---

v2.0.64+에서 지원. CLAUDE.md 하나로 부족할 때 도메인별로 규칙을 나눌 수 있습니다.

## 디렉토리 구조

```
.claude/
├── CLAUDE.md              # 핵심 내용만 (30줄 이하)
├── rules/
│   ├── code-style.md      # 코드 스타일 규칙
│   ├── testing.md         # 테스팅 전략
│   ├── security.md        # 보안 가이드
│   └── workflows/
│       └── api-creation.md # API 생성 워크플로우
└── skills/
    └── my-skill/
        └── SKILL.md
```

## 핵심 장점

- **자동 로드**: `rules/` 디렉토리의 파일은 CLAUDE.md와 동일한 우선순위로 자동 로드
- **경로 기반 조건부 적용**: YAML frontmatter의 `paths` 필드로 특정 파일 패턴에만 규칙 적용
- **충돌 없는 팀 편집**: 프론트엔드/백엔드 팀이 각각의 규칙 파일을 독립적으로 관리

## 경로 기반 규칙 예시

```yaml
---
paths:
  - "src/backend/**/*.py"
  - "tests/backend/**/*.py"
---

# Backend Python 규칙
- FastAPI 라우트 핸들러 패턴 준수
- Pydantic 모델로 요청/응답 정의
- 비동기 함수 우선 사용
```

```yaml
---
paths:
  - "src/frontend/**/*.tsx"
  - "src/components/**/*.tsx"
---

# Frontend React 규칙
- Server Components 기본
- 'use client'는 인터랙션 필요 시만
- shadcn/ui 컴포넌트 우선 사용
```

## 실전 활용

| 파일 | 용도 | 적용 범위 |
|------|------|-----------|
| `rules/code-style.md` | 네이밍, import 순서 | 전체 |
| `rules/testing.md` | 테스트 전략, 커버리지 | 전체 |
| `rules/security.md` | 인증, 입력 검증 | 전체 |
| `rules/backend/python.md` | FastAPI, Pydantic | `src/backend/**` |
| `rules/frontend/react.md` | React, Next.js | `src/frontend/**` |

예시 파일: [`examples/rules/`](../examples/rules/)

---

[다음: settings.json 설정 관리 →](07-settings.md)
