---
title: "Astro + TailwindCSS로 기술 블로그 만들기"
description: "Astro 프레임워크와 TailwindCSS를 활용해 빠르고 아름다운 기술 블로그를 처음부터 만드는 과정을 공유합니다."
pubDate: 2026-02-22
tags: ["바이브코딩", "웹개발", "Astro"]
heroImage: "../../assets/blog-placeholder-3.jpg"
---

이 블로그 자체가 바이브코딩의 결과물입니다. AI와 대화하며 Astro 프레임워크 기반 블로그를 만들어보았습니다.

## 왜 Astro인가?

Astro는 **콘텐츠 중심 웹사이트**를 위해 설계된 프레임워크입니다. 주요 장점은:

- **제로 JavaScript** — 기본적으로 클라이언트에 JavaScript를 보내지 않아 빠릅니다
- **Content Collections** — Markdown/MDX 콘텐츠를 타입 안전하게 관리합니다
- **Islands Architecture** — 필요한 부분만 인터랙티브하게 만듭니다

## 기술 스택

| 기술           | 역할             |
| -------------- | ---------------- |
| Astro          | 정적 사이트 생성 |
| TailwindCSS v4 | 스타일링         |
| MDX            | 콘텐츠 작성      |
| Vercel         | 배포             |

## 디자인 원칙

이 블로그의 디자인은 세 가지 원칙을 따릅니다:

1. **콘텐츠 퍼스트** — 불필요한 장식을 최소화하고 글에 집중
2. **다크모드 기본 지원** — 어두운 환경에서도 편안한 읽기 경험
3. **반응형** — 모바일에서 데스크톱까지 일관된 경험

## Content Collections 활용

Astro의 Content Collections는 블로그 포스트를 체계적으로 관리할 수 있게 해줍니다:

```typescript
const blog = defineCollection({
  loader: glob({ base: "./src/content/blog", pattern: "**/*.{md,mdx}" }),
  schema: z.object({
    title: z.string(),
    description: z.string(),
    pubDate: z.coerce.date(),
    tags: z.array(z.string()).default([]),
  }),
});
```

스키마를 정의해두면 프론트매터의 타입을 자동으로 검증해주기 때문에, 실수를 줄이고 IDE 자동완성도 활용할 수 있습니다.

## 마무리

이 블로그를 만드는 전체 과정이 바이브코딩으로 진행되었습니다. AI에게 의도를 설명하고, 생성된 코드를 검토하고, 피드백을 주는 반복으로 완성했습니다. 앞으로 이 블로그에서 더 많은 바이브코딩 경험을 공유하겠습니다.
