# 콘텐츠 · 코드 스타일 규칙 (공용)

Codex·Claude 등 모든 에이전트가 이 저장소의 자료를 작성·수정할 때 공통으로 따르는 규칙.

## 언어 · 톤
- 모든 사용자 대면 콘텐츠는 **한국어**. `<html lang="ko">` 유지.
- 톤: 교육적·중립적. 특정 종목/전략의 **수익을 보장하거나 권유하는 표현 금지**.
  ("~하면 번다", "필승", "추천" 등 금지 → "~하는 구조", "예시", "교육용"으로.)
- 3배 레버리지의 **고위험성(원금 전액 손실·변동성 끌림·상장폐지 가능)** 을 항상 함께 서술.

## 사실성 · 출처
- 전략 규칙·수치는 **공개된 2차 자료를 교차검증**해 기술하고, 출처가 상이하면
  "출처마다 상이/불확실"로 표기한다. 추측으로 규칙을 지어내지 않는다.
- 버전(v1/v2.2/v3.0 등)마다 공식이 다르므로 **버전을 명시**하고 섞지 않는다.
- 매매 원장·시뮬레이션은 "교육용 예시(가상 데이터)"임을 캡션/면책에 명시한다.
- 각 페이지 하단에 **출처 목록**을 유지한다.

## 기술 규격 (정적 HTML)
- **빌드 도구 없음.** 순수 HTML + 인라인 `<style>` + 바닐라 `<script>`. 브라우저로 바로 열림.
- **외부 의존성 최소화** (CDN·폰트·트래커 지양). 자기완결적으로 유지.
- **라이트/다크 테마** 모두 지원: `@media (prefers-color-scheme)` + `:root[data-theme]` 유지.
- **반응형**: 표·차트는 `overflow-x:auto` 컨테이너 안에서 가로 스크롤. 본문은 가로 스크롤 금지.
- **접근성**: `:focus-visible` 스타일, 차트 SVG에 `role="img"`·`aria-label`, `prefers-reduced-motion` 존중.
- 숫자는 `font-variant-numeric: tabular-nums` (`.num`/`--mono`) 유지.
- 파일 간 디자인 토큰(CSS 변수) 네이밍을 일관되게 유지.

### 필수 골격 (신규 페이지는 이 템플릿으로 시작)
누락하면 모바일 뷰포트 붕괴·CSP 미적용 등 실제 장애가 발생하므로 전부 필수다.

```html
<!doctype html>
<html lang="ko">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta http-equiv="Content-Security-Policy" content="default-src 'none'; style-src 'unsafe-inline'; img-src 'self' data:; script-src 'unsafe-inline'; base-uri 'none'; form-action 'none'">
<title>…</title>
<style> /* 인라인 스타일 */ </style>
</head>
<body>
<!-- 콘텐츠 -->
<script> /* 바닐라 JS */ </script>
</body>
</html>
```

### 보안 규칙 (어길 시 작업 반려)
- DOM에 마크업을 조립할 때 **`innerHTML` 금지** — `textContent`·`createElement`·
  `replaceChildren`을 사용한다. (현재 코드베이스 innerHTML 사용처 = 0개, 이 상태를 유지)
- HTML 인라인 `on*` 이벤트 속성(`onclick=` 등) 금지 — `addEventListener`만 사용.
- 외부 네트워크 호출 금지(`fetch`·XHR·WebSocket·CDN 스크립트·트래커) —
  위 CSP의 `default-src 'none'`과 정합. 정말 필요해지면 CSP와 함께 이 규칙을 재검토한다.

### JS 변경 시 문법 검증 (브라우저 열기 전 1차 게이트)
`<script>` 내용을 추출해 Node로 컴파일 오류를 먼저 확인한다 (문법 오류를 브라우저로 찾지 않는다):

```bash
node -e 'const fs=require("fs"),vm=require("vm");const h=fs.readFileSync("페이지.html","utf8");
for(const m of h.matchAll(/<script>([\s\S]*?)<\/script>/g)) new vm.Script(m[1]);'
```

## 필수 고지
- 모든 콘텐츠 변경 시 [attribution.md](./attribution.md)의 3가지 고지
  (원작자 명시·교육용 고지·삭제 요청)를 **반드시 유지**한다.

## 검증
- 변경 후 브라우저(또는 `python3 -m http.server`)로 열어 **콘솔 에러 없음**,
  라이트/다크 전환, 차트·표 렌더링, 반응형(모바일 폭)을 확인한다.
- 자동 확인이 필요하면 헤드리스 Chrome으로 렌더링 결과를 덤프해 검사한다
  (JS 생성 콘텐츠가 실제로 DOM에 나타나는지 = CSP가 스크립트를 막지 않는지 포함):

```bash
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless=new \
  --disable-gpu --virtual-time-budget=4000 --enable-logging=stderr --v=0 \
  --dump-dom http://localhost:8000/페이지.html > /tmp/dom.html 2> /tmp/console.log
```
