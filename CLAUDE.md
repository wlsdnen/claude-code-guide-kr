# claude-code-guide-kr

한국어 Claude Code 종합 설정 가이드. 문서 전용 프로젝트.

## 구조
- `docs/` — 15개 섹션별 마크다운 (01-hierarchy ~ 15-faq)
- `examples/` — 복사해서 바로 쓸 수 있는 설정 파일 (CLAUDE.md, settings, mcp, hooks, rules)
- `index.html`, `guide.html` — 동일한 풀 HTML 가이드 (다크 테마). index.html은 GitHub Pages용
- `README.md` — 프로젝트 소개, 읽는 방법, 목차

## 규칙
- 모든 문서는 한국어로 작성
- docs/ 파일은 상단에 네비게이션 링크 포함 (← 목차 / 이전 / 다음 →)
- HTML 수정 시 index.html과 guide.html 둘 다 동일하게 반영
- 예시 파일은 실제 사용 가능한 상태 유지
- 커밋 메시지: Conventional Commits (docs:, fix:, feat:, chore:)

## 주의
- index.html = guide.html (완전 동일 파일). 내용 변경 시 `cp guide.html index.html`로 동기화
- HTML의 .file-tree 클래스는 white-space: pre 필수 (트리 구조 렌더링)
- 외부 링크 추가 시 실제 접속 가능 여부 확인
