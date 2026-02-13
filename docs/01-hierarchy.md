# CLAUDE.md 계층 구조

[← 목차로 돌아가기](../README.md)

---

## 왜 설정 파일이 필요한가?

Claude Code는 설정 없이도 작동합니다. 하지만 CLAUDE.md를 추가하면 프로젝트의 기술 스택과 컨벤션을 알고 코드를 작성합니다. 예를 들어 "Next.js App Router 사용, Server Components 기본"이라고 적어두면, 구식 Pages Router 패턴 대신 올바른 코드가 나옵니다.

## 4단계 계층

Claude Code는 여러 레벨의 설정 파일을 자동으로 읽어들입니다. **더 구체적인 파일이 우선**합니다.

## 4단계 계층

```
~/.claude/CLAUDE.md          [Global]  모든 프로젝트 · 개인 선호도, 보편 원칙
        ↓
./CLAUDE.md                  [Project] 프로젝트별 · 팀 컨벤션, 기술 스택 · Git 커밋
        ↓
.claude/local.md             [Local]   개인 오버라이드 · .gitignore 대상
        ↓
.claude/rules/*.md           [Rules]   모듈형 규칙 (v2.0.64+) · 경로 기반 조건부 적용
```

## 우선순위 규칙

- Local > Project > Global 순으로 우선
- **Deny 규칙이 최우선**
- 서브디렉토리 CLAUDE.md는 해당 영역 작업 시 자동 로드

## 배치 결정 프레임워크

| 내용 | 위치 | 예시 |
|------|------|------|
| 보편적 선호도 | `~/.claude/CLAUDE.md` | "변경 후 테스트 실행", "Conventional Commits" |
| 팀 표준 | `./CLAUDE.md` | "Next.js App Router 사용", "shadcn/ui 컴포넌트" |
| 개인 설정 | `.claude/local.md` | "로컬 DB: localhost:5432" |
| 도메인별 규칙 | `.claude/rules/` | "code-style.md", "testing.md", "security.md" |

## 디렉토리 탐색

Claude Code는 **현재 작업 디렉토리부터 루트까지** CLAUDE.md를 탐색합니다:

```
/home/user/project/src/components/
    → ./CLAUDE.md (components 레벨)
    → ../CLAUDE.md (src 레벨)
    → ../../CLAUDE.md (project 레벨)
    → ~/.claude/CLAUDE.md (global)
```

모노레포에서 특히 유용합니다. 각 패키지/서비스에 독립적인 CLAUDE.md를 둘 수 있습니다.

---

[다음: CLAUDE.md 작성 가이드 →](02-writing-guide.md)
