# Hooks 자동화

[← 목차로 돌아가기](../README.md) · [이전: 스킬 관리](09-skills.md)

---

Hooks는 Claude Code가 특정 동작을 할 때 **자동으로 셸 명령어를 실행하는 기능**입니다. 예를 들어 "파일을 저장할 때마다 자동으로 코드 포맷팅 실행" 같은 자동화를 설정할 수 있습니다. Claude의 판단에 의존하지 않고 **항상 확실하게 실행**됩니다(결정론적 동작).

## 라이프사이클 이벤트

| 이벤트 | 시점 | 주요 용도 |
|--------|------|-----------|
| `PreToolUse` | 도구 실행 전 | 파일 보호, 위험 명령 차단 |
| `PostToolUse` | 도구 실행 후 | 자동 포맷팅, 린트, 테스트 |
| `SessionStart` | 세션 시작 | 환경변수 설정, 초기화 |
| `Stop` | 응답 완료 | 알림 전송, 로깅 |
| `UserPromptSubmit` | 프롬프트 제출 | 입력 검증, 키워드 감지 |
| `Notification` | 입력 필요 | Slack/Discord 알림 |

## 실전 Hooks 예시

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "match": "Write(**.py)",
        "command": "black ${file} && isort ${file}",
        "description": "Python 자동 포맷팅"
      },
      {
        "match": "Write(**.{js,ts,tsx})",
        "command": "prettier --write ${file}",
        "description": "JS/TS 포맷팅"
      }
    ],
    "PreToolUse": [
      {
        "match": "Write(config/production.*)",
        "command": "echo 'Production protected'; exit 1",
        "description": "프로덕션 설정 보호"
      },
      {
        "match": "Write(**)",
        "command": "if grep -q 'API_KEY\\|SECRET' ${file}; then exit 1; fi",
        "description": "민감 데이터 검출"
      }
    ],
    "Stop": [
      {
        "command": "notify-send 'Claude Code' 'Task completed'",
        "description": "Linux 데스크톱 알림"
      }
    ]
  }
}
```

## Hook 환경 변수

- `${file}` — 작업 대상 파일
- `${tool}` — 도구 이름 (Write, Read, Bash 등)
- `$CLAUDE_PROJECT_DIR` — 프로젝트 루트

## Hooks vs 스킬

| | Hooks | 스킬 |
|-|-------|------|
| **실행** | 결정론적 (항상 실행) | Claude 판단 |
| **용도** | 포맷팅, 보호, 알림 | 워크플로우, 프로세스 |
| **트리거** | 이벤트 기반 | 키워드/패턴 기반 |
| **복잡도** | 단순 명령어 | 복잡한 지침 |

> 확정적으로 실행해야 하는 것(포맷팅, 보안 체크)은 Hooks, Claude의 판단이 필요한 것(코드 리뷰, 디버깅)은 스킬.

예시 파일: [`examples/hooks.json`](../examples/hooks.json)

---

[다음: Dotfiles & 크로스 환경 동기화 →](11-dotfiles.md)
