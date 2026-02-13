# examples/ 에이전트 가이드

바로 복사해서 사용할 수 있는 Claude Code 설정 예시 파일들.

## 파일 목적
| 파일 | 복사 위치 | 설명 |
|------|-----------|------|
| `global-claude.md` | `~/.claude/CLAUDE.md` | 글로벌 개인 선호도 |
| `project-claude.md` | `./CLAUDE.md` | 프로젝트별 설정 |
| `settings.json` | `~/.claude/settings.json` | 권한, 환경변수, 훅 |
| `mcp.json` | `~/.claude/.mcp.json` | MCP 서버 연결 |
| `hooks.json` | settings.json hooks 섹션 참고용 | 훅 설정 예시 |
| `rules/*.md` | `.claude/rules/` | 모듈형 규칙 |

## 수정 규칙
- 모든 예시는 실제 사용 가능한 상태 유지
- JSON 파일은 유효한 JSON 형식
- API 키는 `${ENV_VAR}` 환경변수 참조 사용 (하드코딩 금지)
- 수정 후 README.md의 설명도 함께 업데이트
