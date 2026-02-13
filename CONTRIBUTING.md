# 기여 가이드

이 가이드를 더 좋게 만드는 데 관심을 가져주셔서 감사합니다!

## 기여 방법

### 1. 이슈 등록

- 오류나 구식 정보를 발견하면 [이슈](../../issues)를 등록해주세요
- 새로운 섹션이나 팁 제안도 환영합니다

### 2. Pull Request

1. 이 레포를 Fork합니다
2. 새 브랜치를 만듭니다: `git checkout -b feature/my-contribution`
3. 변경사항을 커밋합니다: `git commit -m "docs: 새로운 팁 추가"`
4. Push합니다: `git push origin feature/my-contribution`
5. Pull Request를 생성합니다

### PR 가이드라인

- **한국어**로 작성해주세요
- 커밋 메시지는 [Conventional Commits](https://www.conventionalcommits.org/) 형식:
  - `docs:` 문서 수정/추가
  - `fix:` 오류 수정
  - `feat:` 새 섹션/기능 추가
  - `chore:` 구조 변경, 포맷팅
- 가능하면 **출처 링크**를 포함해주세요
- 예시 파일 변경 시 실제 사용 가능한지 확인해주세요

## 기여 가능한 영역

### 내용 추가
- 새로운 커뮤니티 팁이나 워크플로우
- 엔터프라이즈 사용 사례
- 스택별 CLAUDE.md 예시 (Python/Django, Go, Rust 등)
- 새로운 MCP 서버 소개

### 개선
- 구식 정보 업데이트 (Claude Code 버전 변경 시)
- 오타 및 문법 수정
- 더 나은 예시 코드
- 가독성 개선
- 외부 링크 검증 (특히 `docs/14-resources.md`의 URL이 유효한지 확인)

### 번역
- 영문 버전 작성 (`docs/en/` 디렉토리)

## 스타일 가이드

- 마크다운 파일은 한 줄에 하나의 문장
- 코드 블록에는 언어 태그 명시 (```json, ```bash 등)
- 링크는 상대 경로 사용 (`../examples/` 등)
- 각 docs 파일 상단에 네비게이션 링크 포함

## 질문이 있으시면

이슈를 등록하거나 디스커션에 질문해주세요. 모든 기여를 환영합니다!
