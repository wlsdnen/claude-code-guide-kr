# FAQ & 트러블슈팅

[← 목차로 돌아가기](../README.md) · [이전: 참고 리소스](14-resources.md)

---

자주 묻는 질문과 흔한 문제 해결 방법을 모았습니다.

## CLAUDE.md 관련

### CLAUDE.md를 만들었는데 Claude가 무시하는 것 같아요

- **파일 위치 확인**: 프로젝트 루트에 `CLAUDE.md`가 있는지 확인. 파일명 대소문자 주의
- **길이 확인**: 80줄을 넘으면 뒷부분이 무시될 수 있음. 60줄 이하 권장
- **확인 방법**: Claude Code에서 "CLAUDE.md 내용을 요약해줘"라고 물어보세요
- **충돌 확인**: 글로벌(`~/.claude/CLAUDE.md`)과 프로젝트 CLAUDE.md가 상충하는 내용이 없는지 확인

### CLAUDE.md 규칙을 Claude가 어길 때

- 같은 규칙을 다른 표현으로 **2~3번 반복**하면 준수율이 높아집니다
- "~하지 마라"보다 "~대신 ~해라"가 더 효과적
- 세션이 길어지면 `/compact`로 컨텍스트를 압축하세요

## 세션 관련

### 세션이 느려졌어요

1. `/compact` — 컨텍스트를 요약하여 토큰 절약
2. `/clear` — 새 세션으로 시작 (가장 효과적)
3. CLAUDE.md 줄 수 확인 — 300줄 이상이면 대폭 축소

### Claude가 같은 실수를 반복해요

- **2회 실패 후 `/clear`**: 실패한 시도가 컨텍스트에 쌓여 반복 유발
- 새 세션에서 더 구체적인 프롬프트로 재시도
- 반복되는 실수는 CLAUDE.md에 "절대 ~하지 말 것" 추가

## MCP 관련

### MCP 서버 연결이 안 돼요

```bash
# 1. 서버 목록 및 상태 확인
claude mcp list

# 2. 특정 서버 로그 확인
claude mcp logs [서버이름]

# 3. 환경변수 확인 (API 키가 설정되어 있는지)
echo $GITHUB_TOKEN
echo $BRAVE_API_KEY
```

- `.mcp.json`의 JSON 문법 오류 확인 (쉼표, 괄호)
- `npx` 명령이 작동하는지 확인: `npx -y @modelcontextprotocol/server-github --help`
- 환경변수는 `~/.bashrc` 또는 `~/.zshrc`에 `export`로 설정

## 비용 관련

### 비용이 너무 많이 나와요

1. **모델 전환**: 단순 작업은 `/model haiku` (Sonnet 대비 1/3 비용)
2. **CLAUDE.md 축소**: 매 메시지마다 포함되므로 짧을수록 절약
3. **`/compact` 습관화**: 긴 세션의 토큰 비용 40~80% 절감
4. **`/clear` 활용**: 주제가 바뀌면 새 세션 시작
5. **`/cost`로 모니터링**: 현재 세션 사용량 실시간 확인

### 비용 절감 효과를 어떻게 측정하나요?

- `/cost` — 현재 세션 토큰 사용량
- `/stats` — 누적 사용 패턴 분석
- 일반적으로 하루 평균 $6, 상위 10%가 $12 정도

## Hooks 관련

### Hook이 실행되지 않아요

- `settings.json`의 `hooks` 섹션 JSON 문법 확인
- `match` 패턴이 실제 도구 호출과 일치하는지 확인 (예: `Write(**.py)`)
- Hook 명령어가 시스템에 설치되어 있는지 확인 (예: `prettier`, `black`)
- `command` 에서 직접 실행해보기: 터미널에서 해당 명령어 테스트

## 기타

### `/init`으로 만든 CLAUDE.md가 너무 길어요

`/init`이 자동 생성한 CLAUDE.md는 출발점일 뿐입니다. 반드시 **60줄 이하로 축소**하세요:
1. Claude가 이미 올바르게 하는 것 삭제
2. 린터가 처리하는 스타일 규칙 삭제
3. 자명한 내용 ("좋은 코드를 작성하라") 삭제
4. [02-작성 가이드](02-writing-guide.md)의 효율성 자가 진단 활용

### 모노레포에서 CLAUDE.md를 어떻게 관리하나요?

각 패키지/서비스 디렉토리에 독립 CLAUDE.md를 두면 됩니다. Claude Code는 현재 작업 디렉토리부터 루트까지 CLAUDE.md를 자동 탐색합니다. 자세한 내용은 [01-계층 구조](01-hierarchy.md)를 참고하세요.

---

> 여기서 해결되지 않는 문제는 [Anthropic 공식 문서](https://code.claude.com/docs/)를 참고하거나, [GitHub 이슈](https://github.com/anthropics/claude-code/issues)에서 검색해보세요.
