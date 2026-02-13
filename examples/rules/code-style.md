# 코드 스타일 규칙

## 네이밍
- 변수/함수: camelCase
- 클래스/타입: PascalCase
- 상수: UPPER_SNAKE_CASE
- 파일: kebab-case (컴포넌트 제외)
- React 컴포넌트 파일: PascalCase.tsx

## Import 순서
1. Node.js 내장 모듈
2. 외부 패키지
3. 내부 모듈 (@ alias)
4. 상대 경로
5. 타입 import (type 키워드 사용)

## 함수
- 화살표 함수 선호 (단, React 컴포넌트는 function 선언)
- 순수 함수 우선
- 함수 길이 50줄 이하 권장
- 파라미터 3개 초과 시 객체로 묶기

## 타입
- `any` 사용 금지 (unknown 대신 사용)
- 모든 public 함수에 명시적 반환 타입
- interface 우선 (type은 union/intersection에만)
