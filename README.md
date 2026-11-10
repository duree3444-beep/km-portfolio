# 이규찬 — Developer Portfolio

HTML5 + CSS3만으로 만든 원페이지 개발자 포트폴리오입니다. JavaScript, 빌드 도구, 외부 CDN 의존성이 없습니다.

## 구성

```text
index.html       # 상단 메뉴 · 첫 화면(설계 보드) · 강점 · 프로젝트 · 일하는 방식 · 기술 · 연락
assets/images/   # 직접 그린 장식용 SVG 일러스트
assets/projects/ # 프로젝트 대표 이미지 (anok / local-llm / knowledge-base .webp)
css/style.css    # 토큰 → 기본 → 레이아웃 → 섹션별 스타일 → 반응형 → 모션
```

## 실행 / 배포

- 로컬: `index.html`을 브라우저로 열면 됩니다.
- 배포: 폴더 그대로 정적 호스팅(GitHub Pages, Netlify 등)에 업로드합니다.

## 수정 위치

- 연락처: `index.html`의 `mailto:` 링크 (좌측 프로필, Contact 섹션 두 곳)
- 프로젝트 이미지를 바꾸려면 `assets/projects/`의 같은 이름 파일을 교체하면 됩니다 (16:9 비율 권장).
- GitHub 링크를 추가하려면 `#contact` 섹션의 이메일 버튼 옆에 같은 형태로 넣으면 됩니다.
