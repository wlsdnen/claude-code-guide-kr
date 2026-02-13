# MCP 서버 관리

[← 목차로 돌아가기](../README.md) · [이전: settings.json](07-settings.md)

---

MCP(Model Context Protocol)는 Claude Code에 외부 도구를 연결하는 표준 방식입니다. 기본 상태에서는 코드 편집과 터미널 명령만 가능한데, MCP 서버를 연결하면 GitHub PR 관리, 웹 검색, 데이터베이스 조회도 할 수 있습니다.

## 필수 MCP 서버 Top 5

| 순위 | 서버 | 용도 |
|------|------|------|
| 1 | **GitHub** | PR/이슈 관리, CI/CD 트리거 |
| 2 | **Context7** | 최신 프레임워크 문서 실시간 fetch. 할루시네이션 방지 |
| 3 | **Sequential Thinking** | 구조화된 문제 해결 프로세스 |
| 4 | **Brave Search** | 웹 검색 및 실시간 리서치 |
| 5 | **Puppeteer** | 브라우저 자동화, 스크린샷, E2E 테스트 |

## MCP 설정 파일 (.mcp.json)

```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": { "GITHUB_TOKEN": "${GITHUB_TOKEN}" }
    },
    "context7": {
      "command": "npx",
      "args": ["-y", "@context7/mcp-server"]
    },
    "brave-search": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-brave-search"],
      "env": { "BRAVE_API_KEY": "${BRAVE_API_KEY}" }
    }
  }
}
```

## 설정 위치

| 위치 | 범위 | 용도 |
|------|------|------|
| `~/.claude/.mcp.json` | 전역 | 모든 프로젝트에서 사용할 MCP |
| `./.mcp.json` | 프로젝트 | 해당 프로젝트에서만 활성화 |

> 프로젝트 `.mcp.json`은 Git에 커밋하여 팀과 공유할 수 있습니다. 단, API 키는 `${ENV_VAR}` 참조를 사용하세요.

## 추가 추천 MCP 서버

| 서버 | 용도 |
|------|------|
| PostgreSQL | 자연어 데이터베이스 쿼리 |
| Filesystem | 로컬 파일 시스템 제어 |
| Notion | 프로젝트 문서 및 태스크 동기화 |
| Google Workspace | Sheets/Drive/Gmail/Calendar 연동 |
| Supabase | 백엔드 서비스 연동 |
| Connect-apps | 500개 이상 서비스 연동 |

## MCP 디버깅

MCP 서버 연결 문제 시:

```bash
# MCP 서버 상태 확인
claude mcp list

# 특정 서버 로그 확인
claude mcp logs github
```

예시 파일: [`examples/mcp.json`](../examples/mcp.json)

---

[다음: 스킬 관리 →](09-skills.md)
