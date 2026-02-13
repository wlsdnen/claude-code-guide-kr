# E-Commerce Platform

## Overview
Next.js 14 기반 전자상거래 플랫폼. App Router 사용.

## Tech Stack
- Next.js 14 (App Router) + TypeScript (strict)
- Prisma + PostgreSQL, Tailwind CSS, Zod

## Architecture
- /app - Pages, layouts, API routes
- /components - 재사용 컴포넌트
- /lib - 유틸리티 및 DB 클라이언트
- /prisma - DB 스키마

## Commands
- npm run dev        # localhost:3000
- npm test           # Jest + RTL
- npm run db:push    # Prisma 스키마 푸시
- npm run lint       # ESLint + Prettier

## Conventions
- Server Components 기본, 인터랙션 필요 시만 'use client'
- DB 쿼리는 /lib/queries에 분리
- Zod 스키마로 모든 입력 검증

## Important
- 결제 코드는 /lib/payments 에서만 수정
- 환경 변수는 .env.example 참고
