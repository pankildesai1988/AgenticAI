# ADR-0001 — Repository Structure Decision
DATE=2026-05-24
STATUS=ACCEPTED

## Decision
Use AgenticAI GitHub repo with 00-09 numbered folder system.

## Why
- Numbered folders = natural load order for AIs
- 00-system loads first = brainstem always available
- Separated governance (00) from content (02-09)
- Matches agentic system design pattern

## Alternatives Considered
- Flat structure → rejected: no load order, grows messy
- Wiki → rejected: no git versioning, bad for AI context loading

## Impact
All future phases follow same folder convention.
