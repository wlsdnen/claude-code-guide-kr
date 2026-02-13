# Dotfiles & 크로스 환경 동기화

[← 목차로 돌아가기](../README.md) · [이전: Hooks](10-hooks.md)

---

여러 머신에서 일관된 Claude Code 환경을 유지하는 방법입니다.

## 권장 Dotfiles 구조

```
~/dotfiles/
├── README.md
├── install.sh              # 자동 설치 스크립트
├── .gitignore
├── claude/
│   └── .claude/
│       ├── settings.json
│       ├── CLAUDE.md
│       ├── .mcp.json       # MCP 서버
│       ├── skills/         # 커스텀 스킬
│       ├── hooks/          # 커스텀 훅
│       └── rules/          # 모듈형 규칙
├── zsh/
│   └── .zshrc
└── git/
    └── .gitconfig
```

## 심볼릭 링크 설치

```bash
#!/bin/bash
# install.sh

# 기존 설정 백업
[ -d ~/.claude ] && mv ~/.claude ~/.claude.bak.$(date +%Y%m%d)

# 심볼릭 링크 생성
ln -sf ~/dotfiles/claude/.claude ~/.claude

# 또는 GNU Stow 사용 (권장)
cd ~/dotfiles && stow claude
```

### GNU Stow를 권장하는 이유

> GNU Stow는 심볼릭 링크를 자동 관리하는 경량 도구입니다. `sudo apt install stow` (Ubuntu) 또는 `brew install stow` (macOS)로 설치합니다.

- **자동 심볼릭 링크 관리**: `stow claude`만으로 모든 링크 생성
- **충돌 감지**: 기존 파일이 있으면 경고
- **쉬운 제거**: `stow -D claude`로 깔끔하게 제거
- **표준 도구**: 대부분의 Linux/macOS에서 사용 가능

## .gitignore 필수 항목

```gitignore
# 절대 커밋 금지
.credentials.json
*.local.json
*.local.md
.env*

# 대화 히스토리 (프라이버시)
projects/

# 캐시
*.log
statsig/
```

## 커뮤니티 동기화 도구

| 도구 | 설명 |
|------|------|
| [brianlovin/claude-config](https://github.com/brianlovin/claude-config) | 7개 스킬 + sync.sh 양방향 동기화 |
| [claude-code-config-sync](https://www.npmjs.com/package/claude-code-config-sync) | npm 패키지로 설정 동기화 자동화 |
| [ccms](https://github.com/miwidot/ccms) | Claude Code Machine Sync — 머신 간 설정 관리 |
| [claude-code-sync](https://github.com/perfectra1n/claude-code-sync) | Rust CLI로 대화 히스토리 동기화 |

## 새 머신 설정 체크리스트

1. dotfiles 레포 클론
2. `install.sh` 실행 (또는 `stow claude`)
3. 환경 변수 설정 (`GITHUB_TOKEN`, `BRAVE_API_KEY` 등)
4. `claude` 실행하여 인증
5. `/doctor` 실행하여 설정 검증

---

[다음: 비용 최적화 →](12-cost-optimization.md)
