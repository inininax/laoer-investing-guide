# AGENTS.md

> 이 파일은 이 저장소에서 작업하는 **모든 AI 코딩 에이전트의 정본(canonical) 안내서**입니다.
> **Codex, Claude Code, Cursor 등이 모두 같은 내용을 읽습니다.**
>
> **`CLAUDE.md`는 이 파일(`AGENTS.md`)을 가리키는 심볼릭 링크입니다** — 디스크상 실제 파일은
> 하나뿐이고 이름만 둘입니다. 따라서 두 문서가 서로 다르게 갈라질(drift) 수 없습니다.
> 규칙은 항상 여기(그리고 `docs/rules/`)에서만 관리하세요. `CLAUDE.md`를 따로 수정하면
> 곧 이 파일을 수정하는 것과 같습니다.
>
> <sub>심링크 재생성이 필요하면: `rm CLAUDE.md && ln -s AGENTS.md CLAUDE.md`
> (Windows에서 심링크가 깨지면 `CLAUDE.md`에 `@AGENTS.md` 한 줄만 두는 import 방식으로 대체 가능.)</sub>

## 프로젝트 개요

**라오어 투자 전략 교육 자료 (Laoer Investing Guide)** — 필명 「라오어」가 공개한 두 가지
미국주식 투자법(**무한매수법**, **밸류 리밸런싱**)을 규칙과 예시 데이터로 정리한
**교육용 정적 웹 자료** 모음입니다.

- **원저작권자:** 필명 라오어 (이 저장소는 원작자와 무관한 비공식 학습 정리본)
- **성격:** 원저서를 읽고 학습·정리하는 차원의 **2차 교육 자료** (투자 권유 아님)
- **빌드 없음:** 순수 HTML/CSS/JS — 브라우저로 바로 열림

## 저장소 구조

```
index.html               # 랜딩(허브) — 두 자료로 이동
infinite-buying.html     # 무한매수법 (Infinite Buying) — 규칙·SOXL 매매 샘플 원장
value-rebalancing.html   # 밸류 리밸런싱 (Value Rebalancing, VR) — 개념·시뮬레이션
README.md                # 프로젝트 소개·보는 법·출처·삭제 요청 안내
AGENTS.md                # (이 파일) 에이전트 공용 정본 안내서 — 유일한 실제 파일
CLAUDE.md → AGENTS.md    # 심볼릭 링크 (Claude Code용, 내용은 AGENTS.md와 100% 동일)
docs/rules/              # 에이전트 공용 규칙 (아래 참조)
```

각 HTML은 자기완결형입니다: `<style>`와 `<script>`가 파일 안에 인라인되어 있고,
차트는 바닐라 JS로 SVG를 그립니다. 외부 라이브러리/빌드 파이프라인이 없습니다.

## 개발 · 실행

```bash
# 로컬 미리보기
python3 -m http.server 8000    # → http://localhost:8000
# 또는 index.html을 브라우저로 바로 열기

# 배포: GitHub Pages (Settings → Pages → Source: main / root)
# → https://kyungseok-lee.github.io/laoer-investing-guide/
```

빌드·테스트·린트 도구는 없습니다. **검증 = 브라우저로 직접 열어 확인** (콘솔 에러 없음,
라이트/다크 전환, 차트·표 렌더링, 모바일 폭 반응형).

## 공용 규칙 (반드시 준수)

작업 전 아래 규칙 문서를 읽고 따르세요. Codex·Claude 공통입니다.

- **[docs/rules/attribution.md](docs/rules/attribution.md)** — ⭐ 원작자 명시 · 교육용 고지 ·
  삭제 요청 정책. **모든 콘텐츠에 3가지 고지를 반드시 유지.** (이 저장소의 최상위 규칙)
- **[docs/rules/content-style.md](docs/rules/content-style.md)** — 콘텐츠 톤·사실성·출처,
  정적 HTML 기술 규격(테마/반응형/접근성), 검증 방법.

### 핵심 요약 (어길 시 작업 반려)
1. 두 전략의 **원저자가 필명 라오어**임과 원전 저서를 명시한다.
2. 이 자료가 **비공식·교육용 2차 정리물**이며 투자 권유가 아님을 고지한다.
3. **원작자/권리자가 원하면 즉시 삭제**한다는 문구를 유지한다.
4. 규칙·수치는 **교차검증**하고 **버전을 명시**하며, 불확실하면 그렇게 표기한다.
5. 3배 레버리지의 **고위험성**을 항상 함께 서술한다.

## 커밋

- 명확하고 간결한 한국어 커밋 메시지. 논리 단위로 원자적 커밋.
- 커밋/푸시는 사용자가 요청할 때만 수행한다.
