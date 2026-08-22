# AI rules directory (extension point)

This directory holds topic-scoped AI rules beyond the root `AGENTS.md`.
OpenCode picks up every `*.md` here automatically via the glob in
`opencode.json`. Other tools read `AGENTS.md`, which links to these files
and imports them.

## Tool wiring map

| Tool | Reads | Mechanism |
|---|---|---|
| Codex CLI / newer Cursor | `AGENTS.md` | native auto-load |
| OpenCode | `.agents/rules/**/*.md` | `instructions` glob in `opencode.json` |
| Claude Code | `CLAUDE.md` -> `AGENTS.md` | `@AGENTS.md` import file; `@.agents/rules/*.md` lines inside AGENTS.md |
| Gemini CLI | `GEMINI.md` -> `AGENTS.md` | `@AGENTS.md` import file |
| GitHub Copilot | `.github/copilot-instructions.md` | pointer doc referencing AGENTS.md |

## How to add a new rule

1. Create `<topic>.md` in this directory (e.g. `deployment.md`).
   Keep it short, factual, and verified against the code.
2. Add to root `AGENTS.md` 공용 규칙 section:
   - one bullet with a readable link: `[<제목>](.agents/rules/<topic>.md) — 요약`
   - one import line right below it: `@.agents/rules/<topic>.md`
     (Claude Code resolves the import; other agents see a pointer.)
3. OpenCode needs no change — the glob picks the file up automatically.
   Tool entry points (`CLAUDE.md`·`GEMINI.md`·copilot pointer) never need edits.

Never edit through the thin entry-point files (`CLAUDE.md`, `GEMINI.md`);
always edit the source (`AGENTS.md` or files in this directory).

## Existing rules

- `attribution.md` — 원작자 명시 · 교육용 고지 · 삭제 요청 (최상위 규칙)
- `content-style.md` — 콘텐츠·코드 스타일, 필수 HTML 골격, 보안 규칙, 검증 방법
