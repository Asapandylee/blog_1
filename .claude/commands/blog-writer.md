# Blog Writer - 블로그 글쓰기 스킬

블로그 포스트를 작성하는 스킬입니다. 주제를 입력하면 블로그 글을 생성합니다.

## 사용법
`/blog-writer [주제]` 또는 `/blog-writer` (주제 미입력 시 질문)

## 입력
$ARGUMENTS

## 실행 절차

### 1단계: 주제 확인
- `$ARGUMENTS`가 비어있으면 AskUserQuestion으로 주제를 물어봅니다.
- 주제가 있으면 바로 2단계로 진행합니다.

### 2단계: 글 구성 계획
AskUserQuestion으로 다음을 확인합니다:

**질문 1 - 글 스타일:**
- 튜토리얼 (단계별 가이드)
- 인사이트 (경험/의견 공유)
- 리뷰/비교 (도구/기술 비교)
- 뉴스/트렌드 (최신 동향 분석)

**질문 2 - 분량:**
- 짧게 (1000자 내외, 3-5분 읽기)
- 보통 (2000자 내외, 7-10분 읽기)
- 길게 (3000자 이상, 15분+ 읽기)

### 3단계: 블로그 글 작성
아래 규칙을 따라 마크다운 파일을 생성합니다.

#### Frontmatter 규칙
```yaml
---
title: "제목 - 부제목 형식 권장"
description: "1-2문장으로 글의 핵심 요약 (SEO용, 120자 내외)"
pubDate: YYYY-MM-DD  # 오늘 날짜
heroImage: "https://images.unsplash.com/photo-XXXXX?auto=format&fit=crop&w=1200&q=80"
tags: ["태그1", "태그2", "태그3"]  # 2-5개, 기존 태그 우선 재사용
---
```

#### 콘텐츠 규칙
- **언어**: 한국어
- **어조**: 친근하지만 전문적 (반말 X, 지나친 존대 X, "~입니다/~합니다" 체)
- **저자 관점**: Andy (건설 엔지니어, AI/바이브코딩에 관심)
- **핵심 주제**: 건설산업 x AI x 바이브코딩 교차점
- **구조**:
  - 도입부: 독자의 관심을 끄는 질문이나 상황 제시
  - 본문: `##` 소제목으로 구분, 핵심 내용을 논리적으로 전개
  - 코드 예시: 실용적인 코드 스니펫 포함 (해당 시 )
  - 마무리: 핵심 정리 + 독자에게 행동 유도 (CTA)
- **포맷팅**:
  - `**굵은 글씨**`로 핵심 키워드 강조
  - 리스트(`-`)와 번호 목록(`1.`)을 적극 활용
  - 코드 블록에 언어 지정 (```python, ```javascript 등)

#### 파일명 규칙
- 영문 kebab-case: `주제-키워드.md`
- 예: `ai-tools-for-construction-engineers.md`

#### 기존 태그 참고 (재사용 권장)
기존 포스트에서 사용된 태그를 먼저 확인하고, 가능하면 재사용합니다.
새 태그가 필요한 경우에만 추가합니다.

### 4단계: Unsplash 히어로 이미지 선정

글 주제에 어울리는 Unsplash 이미지를 찾아 heroImage로 설정합니다.

#### 이미지 검색 방법
1. WebSearch로 `site:unsplash.com/photos [주제 관련 영문 키워드]`를 검색합니다.
2. 검색 결과에서 Unsplash 사진 URL(https://unsplash.com/photos/...)을 찾습니다.
3. **중요**: Unsplash 페이지 slug(예: `wjFOjA2zXy8`)는 이미지 URL과 다릅니다!
   Bash의 curl로 실제 이미지 ID를 추출합니다:
   ```bash
   curl -s "https://unsplash.com/photos/{slug}" | grep -o 'https://images.unsplash.com/photo-[^"?]*' | head -1
   ```
4. 추출된 실제 이미지 ID로 URL을 구성합니다:
   ```
   https://images.unsplash.com/photo-{실제숫자ID}?auto=format&fit=crop&w=1200&q=80
   ```
5. curl -sI로 URL이 200 응답을 반환하는지 반드시 검증합니다.

#### 주제별 검색 키워드 가이드
| 글 주제 | 추천 검색어 |
|---------|------------|
| 건설/현장 | construction site, building, architecture, crane |
| AI/머신러닝 | artificial intelligence, machine learning, robot, neural network |
| 코딩/개발 | coding, programming, developer, computer screen |
| 데이터/분석 | data analytics, dashboard, chart, spreadsheet |
| 자동화/업무 | automation, workflow, office, productivity |
| 건설 x AI | smart building, digital construction, BIM |

#### 이미지 선정 기준
- 가로형(landscape) 이미지 선택 (블로그 레이아웃에 적합)
- 밝고 선명한 이미지 우선
- 글 주제와 직접적으로 연관되는 이미지
- 텍스트가 적거나 없는 이미지 선호

#### 기존 프로젝트의 Unsplash 사용 패턴
이 프로젝트는 heroImage에 Unsplash URL을 직접 사용합니다:
```yaml
heroImage: "https://images.unsplash.com/photo-1531482615713-2afd69097998?auto=format&fit=crop&w=1200&q=80"
```
파라미터: `auto=format&fit=crop&w=1200&q=80` (반드시 포함)

### 5단계: 파일 생성
- `src/content/blog/` 디렉토리에 마크다운 파일을 생성합니다.
- 생성 후 사용자에게 제목, 파일 경로, 태그, heroImage URL, 글 미리보기(첫 3줄)를 보여줍니다.

### 6단계: 검수
- `npm run build` 실행하여 빌드 에러가 없는지 확인합니다.
- 에러가 있으면 자동으로 수정합니다.

## 참고사항
- 기존 포스트 스타일을 참고하여 일관성을 유지합니다.
- SEO를 고려하여 title과 description을 작성합니다.
- 코드 예시는 실제로 동작하는 코드를 작성합니다.
- heroImage는 반드시 Unsplash에서 주제에 맞는 이미지를 찾아 설정합니다.
