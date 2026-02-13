# Claude Code 종합 설정 가이드 🇰🇷

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Claude Code](https://img.shields.io/badge/Claude_Code-2026-blueviolet)](https://code.claude.com)
[![Korean](https://img.shields.io/badge/lang-한국어-red)](README.md)

> CLAUDE.md 작성법부터 플러그인/MCP/스킬 관리, 크로스 환경 동기화까지 — 한국어로 정리된 실전 가이드

Claude Code를 효과적으로 사용하기 위한 종합 설정 가이드입니다.

---

## 읽는 방법

**웹에서 한눈에 보기 (추천)**

> 전체 내용을 한 페이지에서 보고 싶다면 웹 가이드를 이용하세요.
>
> **👉 [https://wlsdnen.github.io/claude-code-guide-kr/](https://wlsdnen.github.io/claude-code-guide-kr/)**

**GitHub에서 섹션별로 보기**

> 필요한 부분만 골라 읽고 싶다면 아래 목차에서 선택하세요.
> 웹 가이드와 동일한 내용이 섹션별 마크다운 파일(`docs/`)로 분리되어 있습니다.

---

## 처음이신가요?

Claude Code가 처음이라면 이 순서로 읽어보세요:

1. **[CLAUDE.md 계층 구조](docs/01-hierarchy.md)** — 설정 파일이 어디에 있고 어떻게 작동하는지
2. **[CLAUDE.md 작성 가이드](docs/02-writing-guide.md)** — 60줄 안에 효과적으로 작성하는 법
3. **[7가지 안티패턴](docs/04-anti-patterns.md)** — 흔한 실수 피하기
4. **[실전 예시](docs/05-examples.md)** — 복사해서 바로 쓸 수 있는 템플릿

이미 사용 중이라면 → [비용 최적화](docs/12-cost-optimization.md), [Hooks 자동화](docs/10-hooks.md), [커뮤니티 팁](docs/13-community.md)

---

## 목차

### 📝 CLAUDE.md 기본기

| # | 주제 | 핵심 내용 |
|---|------|-----------|
| 01 | [계층 구조](docs/01-hierarchy.md) | Global → Project → Local → Rules 우선순위 |
| 02 | [작성 가이드](docs/02-writing-guide.md) | WHY-WHAT-HOW, 60~80줄 제한, 주의 예산 |
| 03 | [포함/제외](docs/03-include-exclude.md) | Progressive Disclosure, 토큰 효율성 |
| 04 | [안티패턴](docs/04-anti-patterns.md) | 과적재, Kitchen Sink, 반복 수정 등 7가지 |
| 05 | [실전 예시](docs/05-examples.md) | 글로벌/프로젝트 CLAUDE.md 전체 예시 |

> 여기서부터는 Claude Code에 좀 익숙해진 후 읽어도 됩니다. 위의 기본기(01~05)만으로도 충분합니다.

### ⚙️ 설정 & 자동화

| # | 주제 | 핵심 내용 |
|---|------|-----------|
| 06 | [모듈화](docs/06-modular-rules.md) | .claude/rules/, 경로 기반 조건부 적용 |
| 07 | [settings.json](docs/07-settings.md) | 5단계 우선순위, 권한 체인 |
| 08 | [MCP 서버](docs/08-mcp.md) | 필수 Top 5, .mcp.json 설정 |
| 09 | [스킬 관리](docs/09-skills.md) | 3-Tier 로딩, SKILL.md 구조 |
| 10 | [Hooks](docs/10-hooks.md) | 6개 이벤트, 자동 포맷팅/보호 |

### 🚀 실전 운영

| # | 주제 | 핵심 내용 |
|---|------|-----------|
| 11 | [Dotfiles](docs/11-dotfiles.md) | GNU Stow, 동기화 도구 |
| 12 | [비용 최적화](docs/12-cost-optimization.md) | 모델 분담, 캐싱, 70% 절감 |
| 13 | [커뮤니티](docs/13-community.md) | Boris Cherny, YK Dojo, 엔터프라이즈 |
| 14 | [리소스](docs/14-resources.md) | 공식 문서, GitHub 레포, 한국어 자료 |
| 15 | [FAQ & 트러블슈팅](docs/15-faq.md) | 자주 묻는 질문, 문제 해결 |

---

## 빠른 시작

### 0. 사전 확인

Claude Code가 설치되어 있어야 합니다. 처음 실행하면 `~/.claude/` 디렉토리가 자동 생성됩니다.

```bash
# Claude Code 설치 확인
claude --version

# ~/.claude/ 디렉토리가 없다면 Claude Code를 한 번 실행
claude
```

> 설치 방법은 [공식 문서](https://code.claude.com/docs/)를 참고하세요.

### 1. 글로벌 CLAUDE.md 설정

[`examples/global-claude.md`](examples/global-claude.md)를 `~/.claude/CLAUDE.md`에 복사하고 커스터마이즈:

```bash
cp examples/global-claude.md ~/.claude/CLAUDE.md
```

### 2. 프로젝트 CLAUDE.md 설정

[`examples/project-claude.md`](examples/project-claude.md)를 프로젝트 루트에 복사:

```bash
cp examples/project-claude.md ./CLAUDE.md
```

### 3. 모듈형 규칙 추가

[`examples/rules/`](examples/rules/)의 파일들을 프로젝트에 복사:

```bash
mkdir -p .claude/rules
cp examples/rules/*.md .claude/rules/
```

> 예시 파일 설명은 [`examples/README.md`](examples/README.md)를 참고하세요.

### 4. 설정 확인

Claude Code를 실행하여 설정이 반영되었는지 확인합니다:

```bash
claude
# 세션에서 "CLAUDE.md 내용을 요약해줘"라고 입력하여 확인
```

---

## 핵심 숫자

| 항목 | 수치 | 출처 |
|------|------|------|
| CLAUDE.md 이상적 길이 | **60줄 이하** | HumanLayer 벤치마크 |
| 안정적 명령어 수 | **150~200개** | 커뮤니티 테스트 |
| 비용 절감 가능 | **50~90%** | 모델 분담 + 프롬프트 캐싱 조합 |
| 프롬프트 캐싱 절감 | **90%** | Anthropic 공식 |
| 엔터프라이즈 가속 | **2~10x** | Altana 등 공식 사례 |

---

## 문서 구조

```
claude-code-guide-kr/
├── README.md                          # 이 문서
├── CLAUDE.md                          # Claude Code 프로젝트 지침
├── index.html                         # GitHub Pages 진입점 (= guide.html)
├── guide.html                         # 풀 HTML 가이드 (다크 테마)
│
├── docs/                              # 섹션별 분리 문서 (01~15)
│   ├── AGENTS.md                      # docs 에이전트 가이드
│   └── 01-hierarchy.md ~ 15-faq.md
├── examples/                          # 바로 사용 가능한 설정 예시
│   ├── AGENTS.md                      # examples 에이전트 가이드
│   ├── README.md                      # 예시 파일 안내
│   ├── global-claude.md               # 글로벌 CLAUDE.md 템플릿
│   ├── project-claude.md              # 프로젝트 CLAUDE.md 템플릿
│   ├── settings.json                  # settings.json 예시
│   ├── mcp.json                       # MCP 서버 설정 예시
│   ├── hooks.json                     # Hooks 설정 (참고용, settings.json hooks 섹션)
│   └── rules/                         # .claude/rules/ 예시
│
├── CONTRIBUTING.md                    # 기여 가이드
└── LICENSE                            # MIT License
```

---

## 기여하기

이 가이드를 더 좋게 만들어주세요! [CONTRIBUTING.md](CONTRIBUTING.md)를 참고하세요.

- 새로운 팁이나 사례 추가
- 오류 수정 및 최신 정보 업데이트
- 예시 파일 개선
- 번역 (영문 버전)

---

## 참고

이 가이드는 아래 리소스들을 참고하여 작성되었습니다:

- [Anthropic 공식 문서](https://code.claude.com/docs/)
- [awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code)
- [HumanLayer CLAUDE.md 가이드](https://www.humanlayer.dev/blog/writing-a-good-claude-md)
- [Builder.io 완전 가이드](https://www.builder.io/blog/claude-md-guide)

전체 참고 리소스 목록: [docs/14-resources.md](docs/14-resources.md)

---

## License

[MIT](LICENSE) — 자유롭게 사용, 수정, 배포하세요.
