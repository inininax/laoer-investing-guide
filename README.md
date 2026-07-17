# 라오어 투자 전략 교육 자료 (Laoer Investing Guide)

필명 **라오어**가 공개한 두 가지 미국주식 투자법을 규칙과 예시 데이터로 정리한 교육용 웹 자료 모음입니다. 별도 빌드 없이 브라우저에서 바로 열리는 정적 HTML입니다.

## 구성

| 파일 | 전략 | 내용 |
|---|---|---|
| [`index.html`](index.html) | — | 두 자료로 이동하는 랜딩(허브) 페이지 |
| [`infinite-buying.html`](infinite-buying.html) | **무한매수법** (Infinite Buying) | 큰수/작은수 매수 원리, v2.2 별% 공식, SOXL 한 사이클 매매 샘플 원장 |
| [`value-rebalancing.html`](value-rebalancing.html) | **밸류 리밸런싱** (Value Rebalancing, VR) | 목표값 설정과 리밸런싱 원리, 시뮬레이션 예시 |

## 보는 방법

- **로컬:** `index.html`을 브라우저로 엽니다. (혹은 `python3 -m http.server` 후 `localhost:8000`)
- **GitHub Pages:** 저장소 Settings → Pages → Source를 `main` 브랜치 루트로 지정하면 `https://<사용자>.github.io/laoer-investing-guide/` 로 공개됩니다.

각 페이지는 라이트/다크 테마를 모두 지원하며, 인터랙티브 차트와 매매 원장 표를 포함합니다.

## 자료 신뢰 수준

- 규칙 원본은 라오어의 저서와 네이버 카페 글이며, 본 자료는 공개된 2차 자료(블로그·정리글)를 **교차검증**해 재구성했습니다.
- 매매 원장·수치는 검증된 공식으로 계산한 **교육용 시뮬레이션**으로, 실제 체결·수수료·세금·슬리피지를 반영하지 않습니다.
- 세부 규칙(T값 라운딩, 첫날 진입, 매도 후 회차 재계산 등)은 출처마다 차이가 있어, 실제 운용 전 원문 확인이 필요합니다.

## 면책

이 저장소는 **교육 목적**의 정리 자료이며 **투자 권유가 아닙니다.** 무한매수법·밸류 리밸런싱이 다루는 3배 레버리지 ETF는 변동성 끌림·상장폐지 등으로 **원금 전액 손실이 가능한 초고위험 상품**입니다. 모든 투자 판단과 그 결과에 대한 책임은 투자자 본인에게 있습니다.

## 주요 출처

- 라오어, 『라오어의 미국주식 무한매수법』, 알키, 2021
- 라오어, 『라오어의 미국주식 밸류 리밸런싱』, 알키, 2022
- quantstack.app · pbdfinance.com · sweetvi.tistory.com · truedonshow.com 등 커뮤니티 정리글 (교차검증)
- stockanalysis.com · 운용사 보도자료 (SOXL·SOLX 티커·시세 확인)
