# Builder Andy - 기술 블로그

## 프로젝트 개요
건설산업 × AI × 바이브코딩 주제의 개인 기술 블로그. 저자: Andy (건설 엔지니어)

## 기술 스택
- **프레임워크**: Astro 5 (SSG, Content Collections v2 with `glob` loader)
- **스타일링**: Tailwind CSS v4 (`@tailwindcss/vite` 플러그인)
- **언어**: TypeScript (strict mode)
- **콘텐츠**: Markdown/MDX (`src/content/blog/`)
- **폰트**: Wanted Sans Variable (CDN), JetBrains Mono (코드)
- **배포**: Vercel
- **추가**: MDX, Sitemap, RSS, Sharp (이미지 최적화)

## 프로젝트 구조
```
src/
├── components/    # Astro 컴포넌트 (BaseHead, Header, Footer, PostCard, FormattedDate)
├── content/blog/  # 블로그 포스트 (md/mdx)
├── layouts/       # BlogPost.astro (포스트 레이아웃)
├── pages/         # 라우팅 (index, blog/, blog/[...slug], about, rss.xml)
├── styles/        # global.css (커스텀 디자인 시스템)
└── consts.ts      # 사이트 메타 상수 (SITE_TITLE, SITE_DESCRIPTION, SITE_AUTHOR)
public/            # 정적 파일 (favicon, fonts)
```

## 디자인 시스템
- CSS 커스텀 프로퍼티 기반 라이트/다크 모드 (`html.dark` 클래스 토글)
- 기본 테마: 다크 모드 (localStorage 'theme' 키로 관리)
- 색상 네이밍: `--color-ink`, `--color-surface`, `--color-border`, `--color-link` (다크: `--color-dark-*`)
- 타이포그래피: `.prose` 클래스로 블로그 본문 스타일링
- 레이아웃: `max-w-3xl mx-auto px-4` 패턴

## 콘텐츠 스키마 (content.config.ts)
```ts
{ title: string, description: string, pubDate: Date, updatedDate?: Date, heroImage?: image, tags: string[] }
```

## 컨벤션
- 언어: 한국어 (html lang="ko", 날짜 포맷 ko-KR)
- 페이지 컴포넌트: 각 페이지에서 직접 `<html>`, `<head>`, `<body>` 구성
- 스타일: Tailwind 유틸리티 클래스 인라인 + CSS 커스텀 프로퍼티 혼용
- 네비게이션: Header에 '블로그', '소개' 링크 + 다크모드 토글
- 소셜: GitHub, Instagram, Threads, RSS (Footer)

## 명령어
- `npm run dev` — 개발 서버 (localhost:4321)
- `npm run build` — 프로덕션 빌드 (dist/)
- `npm run preview` — 빌드 미리보기

<!-- Source: .ruler/AGENTS.md -->

# AGENTS.md

Centralised AI agent instructions. Add coding guidelines, style guides, and project context here.

Ruler concatenates all .md files in this directory (and subdirectories), starting with AGENTS.md (if present), then remaining files in sorted order.
