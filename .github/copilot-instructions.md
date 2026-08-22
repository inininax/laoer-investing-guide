# GitHub Copilot 저장소 안내

이 저장소의 모든 규칙은 루트의 [`AGENTS.md`](../AGENTS.md) 한 곳에서 관리하는 정본입니다.
작업 전 반드시 `AGENTS.md`와 `docs/rules/`(`attribution.md` · `content-style.md`)를 읽고 따르세요.

## 최소 준수 사항 (상세는 AGENTS.md 참조)

- **고지 3종 유지**: 원작자(필명 라오어) 명시 · 비공식 교육용 고지 · 삭제 요청 안내.
- **기술 골격**: 신규 페이지는 content-style.md의 필수 템플릿(doctype·charset·viewport·CSP 메타)으로 시작.
- **보안**: CSP가 `default-src 'none'`이므로 외부 리소스(CDN·폰트·fetch) 추가 금지.
  DOM 조립은 `innerHTML` 대신 `textContent`/`createElement`, 이벤트는 `addEventListener`.
- **검증**: JS 수정 시 `<script>` 내용을 Node로 문법 확인 후, 헤드리스 Chrome으로 렌더링 확인
  (정확한 명령어는 docs/rules/content-style.md 검증 섹션).
- **커밋**: 한국어 커밋 메시지, 논리 단위 원자적 커밋. 커밋/푸시는 사용자가 요청할 때만.
