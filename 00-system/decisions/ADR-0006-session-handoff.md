# ADR-0006: Single-File Session Handoff Protocol

**Date:** 2026-05-25
**Status:** Accepted
**Decided By:** Pankil + Claude

---

## Context

Claude.AI/chat was losing context between sessions. SESSION START required loading 4+ separate files via web_fetch (CLAUDE.md, current-state.md, ADRs, active-focus.md). Any skipped or failed fetch = partial context = rules forgotten = duplicates created.

Additional problems:
- Two conflicting CLAUDE.md files existed (root 116L vs AI-HANDOFF/CLAUDE.md 37L)
- No CUT_POINT mechanism for mid-topic session breaks
- Rules scattered across CLAUDE.md, ADRs, and memory-rules.md

## Decision

**Single bootstrap file:** `NEXT-SESSION.md` at repo root.
Contains: resume point, identity, all rules, cumulative knowledge, active projects, phase context, session start/end scripts.

**Session start flow (new):**
```
web_fetch: https://raw.githubusercontent.com/pankildesai1988/AgenticAI/main/NEXT-SESSION.md
→ Everything needed is in that file. Read it. Announce resume point. Begin.
```

**Session start flow (old — DEPRECATED):**
```
Step 1: web_fetch CLAUDE.md
Step 2: web_fetch current-state.md
Step 3: browse ADRs folder
Step 4: apply rules
```

**CUT_POINT field:** Required when session breaks mid-topic. Format:
`P[XX]-T[NN]: Covered [A]. NOT YET covered [B]. Next: [first action].`

**Session end:** AI generates full NEXT-SESSION.md content (all fields updated). User commits. No exceptions.

## Rationale

4-step fetch process is unreliable. Any failed fetch = rules lost silently. Single file = atomic context load. Either it works fully or fails visibly.

CUT_POINT enables precise mid-topic resume without re-explaining covered material.

## Consequences

- NEXT-SESSION.md must be committed after every session (discipline required)
- NEXT-SESSION.md grows slightly each phase (update WHAT PANKIL KNOWS section)
- AI-HANDOFF/CLAUDE.md deleted (was duplicate/conflicting)
- AI-HANDOFF/CHATGPT-P0-HANDOFF.md deleted (was legacy duplicate)
- All AI-HANDOFF platform files updated to reference NEXT-SESSION.md
