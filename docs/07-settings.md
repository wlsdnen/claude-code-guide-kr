# settings.json 설정 관리

[← 목차로 돌아가기](../README.md) · [이전: 모듈화](06-modular-rules.md)

---

Claude Code의 핵심 설정 파일. 권한, 플러그인, 환경변수, hooks를 구조화합니다.

## 설정 우선순위 (5단계)

| 순위 | 위치 | 범위 |
|------|------|------|
| 1 | `~/.claude/settings.json` | 전역 (모든 프로젝트) |
| 2 | `.claude/settings.json` | 프로젝트 (팀 공유) |
| 3 | `.claude/settings.local.json` | 프로젝트 개인 |
| 4 | Enterprise Policy | 조직 관리자 |
| 5 | CLI 플래그 | 세션 단위 |

## 권한 체인

우선순위: `deny` > `allow` > `ask` > `default`

```json
{
  "permissions": {
    "allow": [
      "Read(**/*.{js,ts,tsx,json,md})",
      "Bash(npm *)",
      "Bash(git status)",
      "Bash(git diff*)"
    ],
    "deny": [
      "Read(.env*)",
      "Write(node_modules/**)",
      "Bash(rm -rf *)",
      "Bash(git push --force)"
    ],
    "ask": [
      "Bash(git push*)",
      "Bash(git commit*)",
      "Write(package.json)"
    ]
  }
}
```

## 주요 설정 항목

| 키 | 용도 | 예시 |
|----|------|------|
| `permissions` | 도구 권한 관리 | allow/deny/ask 패턴 |
| `env` | 환경 변수 | `{"NODE_ENV": "development"}` |
| `hooks` | 라이프사이클 훅 | PreToolUse, PostToolUse |
| `enabledPlugins` | 플러그인 활성화 | `{"plugin@source": true}` |
| `model` | 기본 모델 | `"sonnet"`, `"opus"` |
| `statusLine` | 상태 표시줄 | 커스텀 명령어 |

## 환경 변수 설정

settings.json의 `env`로 환경 변수를 Claude 세션에 주입:

```json
{
  "env": {
    "GITHUB_TOKEN": "${GITHUB_TOKEN}",
    "NODE_ENV": "development",
    "CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS": "1"
  }
}
```

> `${VAR}` 구문으로 시스템 환경 변수를 참조할 수 있습니다.

예시 파일: [`examples/settings.json`](../examples/settings.json)

---

[다음: MCP 서버 관리 →](08-mcp.md)
