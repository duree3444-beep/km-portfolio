Build a one-page developer portfolio for a Korean backend/AI systems developer. Static site, no backend, no forms, no analytics. All visible copy is Korean — use the copy below verbatim. Do not invent metrics, job titles, companies, testimonials, or a GitHub link.

## Tech
- Next.js (App Router) + Tailwind CSS + shadcn/ui. Single page `app/page.tsx`, split into section components.
- Font: Pretendard (fallback system-ui). Light theme only.
- Animations in CSS/Tailwind only (no Framer Motion). Respect `prefers-reduced-motion`: disable all motion, content stays fully visible.
- Images: I will upload 3 images. Save them as `/public/projects/anok.webp`, `/public/projects/local-llm.webp`, `/public/projects/knowledge-base.webp` and render with `next/image` (16:9, `object-cover`, rounded).

## Design
- Feel: clean "engineering document" look — white background, deep navy text, one strong blue accent. Not a dark neon dev site.
- Colors: bg `#FFFFFF`, soft bg `#F6F8FC`, heading `#0F172A`, body `#1E293B`, muted `#475569`, border `#E2E8F0`, accent `#1D4ED8`, accent soft `#EFF6FF`, success `#047857` on `#ECFDF5`.
- Container max 1200px. Generous section padding (≈104px desktop / 80px mobile). Radius 16–20px on cards, 12px on buttons.
- Section header pattern: small blue eyebrow text + large bold H2 (≈40px).
- Tags/chips are non-interactive (no pointer, no hover). Status badges are text + green dot, never color-only.
- Body text ≥ 17px, line-height ~1.75, `word-break: keep-all` for Korean.

## Layout (top to bottom)

### 1. Sticky header
Left: brand `이규찬.` (the dot in accent blue). Right nav: `강점` `프로젝트` `일하는 방식` `기술` + dark filled pill button `연락`. All are in-page anchor links. On mobile keep all items visible in one row (smaller padding) — no hamburger. Add a 3px blue→cyan reading-progress bar under the header driven by page scroll (CSS `animation-timeline: scroll()` inside `@supports`).

### 2. Hero — two columns (text left, visual right), stacks on mobile
- Background: very light blue gradient (`#EFF6FF` → white) with a subtle dot grid.
- Small line: `안녕하세요, **이규찬**입니다.`
- H1: `복잡한 문제를 구조화하고,` / `실제 작동하는 시스템으로 만듭니다.` — "실제 작동하는 시스템" in accent blue with a highlighter underline that draws in on load.
- Lead: `백엔드와 AI를 연결하는 개발자를 목표로 합니다. 기능보다 먼저 **입력·출력·제약**을 정의하고, 서비스 경계와 데이터 흐름을 설계합니다.`
- Buttons: primary `프로젝트 보기` (→ #projects, light shine sweep on hover), secondary outline `이메일 보내기` (mailto:duree3444@kyungmin.ac.kr).
- Meta list under a divider: `학교 — 경민대학교 컴퓨터소프트웨어`, `관심 분야 — 백엔드 · AI 에이전트 · 시스템 아키텍처`.
- Right visual (decorative, aria-hidden): a white browser-window card titled `ANOK · 시스템 설계` (traffic-light dots in the title bar) containing a small architecture diagram built from boxes:
  `사용자` (dashed) ↓ `API 게이트웨이 · 인증` (filled blue, soft pulsing glow) ↓ [`Spring Boot / 업무 서비스`] [`AI 서비스 / LLM · RAG`] ↓ [`PostgreSQL`] [`Kafka`] [`Vector DB`].
  Arrows are thin blue lines with a glowing dot that travels down them in a loop (staggered).
  Two floating white cards overlap the board edges and bob gently: top-right `8GB` amber badge + `로컬 LLM 아키텍처 / 제약 안에서 설계 중`; bottom-left green pinging dot + `ANOK / 캡스톤 개발 중`.
  Behind the board, a faint node-network line illustration that drifts slowly.
- On load, hero text items fade-up in sequence (≈100ms stagger); the board pops in slightly after.

### 3. 강점 (`#strengths`, soft bg)
Eyebrow `왜 저와 함께해야 할까요`, H2 `팀에 드릴 수 있는 세 가지`. Three cards in a row (1 column on mobile), each: blue rounded-square icon (white line icon), bold title, 1–2 line text, and an arrow link to evidence.
1. `문제를 구조로 바꿉니다` — `요구사항을 받으면 바로 코드를 쓰지 않고, 입력·출력·제약과 책임 경계를 먼저 정리합니다.` → `일하는 6단계 보기` (#approach)
2. `AI를 시스템으로 연결합니다` — `LLM을 단순 호출이 아니라 권한·데이터·백엔드 흐름과 맞물리는 구성 요소로 설계합니다.` → `ANOK 사례 보기` (#project-anok)
3. `제약 안에서 답을 찾습니다` — `8GB VRAM처럼 한정된 자원에서도 동작하도록 처리 단계를 나누고 정보 흐름을 줄입니다.` → `로컬 LLM 사례 보기` (#project-local-llm)
Hover: card lifts, icon tilts slightly, arrow nudges right.

### 4. 프로젝트 (`#projects`)
Eyebrow `대표 작업`, H2 `프로젝트`. Three stacked cards, each split 50/50: image half + short text half. Alternate sides (2nd card image on the right). Mobile: image on top. Keep text SHORT — no long paragraphs.
Each text half: meta line (`번호 · 구분` + status badge), bold title, one-line summary (slightly larger), three checkmark bullets (blue circle check icon), then tech chips. Hover: card border turns light blue + soft shadow, image zooms to 1.05.

| id | meta | status | title | summary | bullets | chips |
|---|---|---|---|---|---|---|
| project-anok | 01 · 캡스톤 프로젝트 | 진행 중 | ANOK | 흩어진 회의·문서·일정·결재를 AI와 백엔드로 하나의 흐름에 연결합니다. | 서비스 분리와 이벤트 기반 연결 / 권한·테넌트별 데이터 격리 / 사내 문서 검색(RAG) | Spring Boot, PostgreSQL, Kafka, Docker, RAG |
| project-local-llm | 02 · 아키텍처 설계 | 설계 중 | 로컬 LLM 아키텍처 | 8GB VRAM 안에서 업무 요청을 처리하도록 단계를 나눠 설계합니다. | 분석 → 검색 → 검증 → 추론 → 실행 / 긴 문맥을 나눠 메모리 한계 극복 / 정보 접근 권한 유지 | 로컬 LLM, RAG, 컨텍스트 관리 |
| project-knowledge-base | 03 · 개인 프로젝트 | 진행 중 | 공학 지식 베이스 | 흩어진 기술 지식을 문제 중심으로 엮어, 필요할 때 바로 찾게 합니다. | 주제·관계·문제 맥락으로 분류 / 구조화된 문서 형식 / 기술 간 연결 탐색 | 데이터 모델링, 정보 검색 |

Image alt texts (Korean): `ANOK 대표 이미지: 회의, 문서, 검색, 일정, AI, 결재 기능이 중앙 시스템에 연결된 모습` / `로컬 LLM 아키텍처 대표 이미지: 로컬 모델 위로 처리 단계가 층층이 쌓인 모습` / `공학 지식 베이스 대표 이미지: 책 위의 두뇌를 중심으로 설계도, 코드, 회로 자료가 연결된 모습`.

### 5. 일하는 방식 (`#approach`, soft bg)
Eyebrow `일하는 방식`, H2 `모든 프로젝트를 같은 순서로 생각합니다`. Ordered list as a 3×2 card grid (2 cols tablet, 1 col mobile). Each card: blue numbered square, bold step name, one question.
1 `문제 정의` — `누가, 왜 불편한가?` · 2 `요구 분석` — `입력·출력·제약은 무엇인가?` · 3 `설계` — `경계·의존성·데이터 흐름은?` · 4 `구현` — `먼저 검증할 최소 기능은?` · 5 `검증` — `예상대로 동작하는가?` · 6 `개선` — `실패에서 무엇을 바꿀까?`
Hover: card lifts, number badge rotates slightly.

### 6. 기술 (`#skills`)
Eyebrow `기술`, H2 `다루는 기술`. Four cards in one row on desktop (2 cols tablet, 1 col mobile), each with a small line icon in a soft-blue square + category name + white outlined chips. No skill bars, no percentages, no years.
- 백엔드 (server icon): Java, Spring Boot, REST API
- 데이터 (database icon): PostgreSQL, MySQL, MongoDB, Vector DB
- 인프라 (cloud icon): Docker, Docker Compose, GitLab CI/CD, Linux, Cloudflare Tunnel
- 아키텍처 · AI (chip icon): MSA, Kafka, LLM, RAG, AI 에이전트

### 7. 연락 (`#contact`)
Full-width blue gradient band (`#1E40AF` → `#2563EB`) with a faint white dot grid. Left: H2 `함께 문제를 풀 개발자를 찾고 계신가요?` + `시스템 설계, 백엔드, AI 서비스에 관한 이야기와 제안을 환영합니다.` Right: large white button showing `duree3444@kyungmin.ac.kr` (mailto). No footer below it.

## Motion summary
- Scroll reveal: section titles, strength cards, project cards, step cards, skill cards, contact content fade-up (≈48px) as they enter the viewport using CSS `animation-timeline: view()` wrapped in `@supports`; without support they simply render visible.
- Hover transitions 150–250ms. Looping animations only inside the hero visual (packets, glow, bob, ping, drift).
- `prefers-reduced-motion: reduce` → no animations, no transitions, smooth scroll off.

## Accessibility & quality
- Semantic landmarks: skip link → header/nav → main (sections with H2) → no extra footer. Exactly one H1. Project titles are H3.
- Visible focus ring (amber, 3px) on all links/buttons. Touch targets ≥ 44px.
- Text contrast ≥ 4.5:1. Decorative visuals `aria-hidden`.
- No horizontal page scroll from 360px to 1920px. `scroll-margin-top` so the sticky header never covers section titles.
- `<html lang="ko">`, title `이규찬 | 백엔드·AI 시스템 개발자 포트폴리오`, meta description `문제를 구조화하고 시스템으로 연결하는 개발자 이규찬의 포트폴리오. ANOK, 로컬 LLM 아키텍처, 공학 지식 베이스 프로젝트를 소개합니다.`
