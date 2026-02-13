# 예시 파일 안내

바로 복사해서 사용할 수 있는 설정 파일들입니다.

## 어디서부터 시작하나요?

**1단계:** 글로벌 CLAUDE.md부터 설정하세요. 모든 프로젝트에 적용됩니다.

```bash
cp global-claude.md ~/.claude/CLAUDE.md
```

**2단계:** 프로젝트별 CLAUDE.md를 추가하세요.

```bash
cp project-claude.md /path/to/your/project/CLAUDE.md
```

**3단계:** 필요에 따라 나머지를 추가하세요.

---

## 파일 설명

| 파일 | 용도 | 복사 위치 |
|------|------|-----------|
| `global-claude.md` | 개인 개발 선호도 (모든 프로젝트 공통) | `~/.claude/CLAUDE.md` |
| `project-claude.md` | 프로젝트별 기술 스택, 명령어, 컨벤션 | `./CLAUDE.md` |
| `settings.json` | 권한, 환경변수, 플러그인 설정 | `~/.claude/settings.json` |
| `mcp.json` | MCP 서버 연결 (GitHub, Context7 등) | `~/.claude/.mcp.json` |
| `hooks.json` | 자동 포맷팅, 파일 보호, 알림 | `~/.claude/settings.json`의 hooks 섹션 |
| `rules/code-style.md` | 코드 스타일 규칙 | `.claude/rules/code-style.md` |
| `rules/testing.md` | 테스팅 전략 | `.claude/rules/testing.md` |
| `rules/security.md` | 보안 규칙 | `.claude/rules/security.md` |

## 주의사항

- 파일을 복사한 후 **반드시 자신의 환경에 맞게 수정**하세요
- `hooks.json`은 독립 파일이 아닌 `settings.json`의 `hooks` 섹션을 별도로 보여주는 **참고용**입니다
- `settings.json`과 `hooks.json`은 실제 도구(prettier, black 등)가 설치되어 있어야 동작합니다
- `mcp.json`의 API 키는 환경 변수로 설정하세요 (`export GITHUB_TOKEN=...`)
