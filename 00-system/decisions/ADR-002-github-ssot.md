# ADR-002: GitHub as Single Source of Truth (SSOT)

**Date:** 2026-05-25 (reconstructed from session history)
**Status:** Accepted
**Decided By:** Pankil + Claude

---

## Context

AI platforms (Claude, ChatGPT, Gemini) have no persistent memory across sessions.
Need a reliable SSOT that any AI can read at session start.

## Decision

**SSOT:** GitHub repo `pankildesai1988/AgenticAI` (public)
**Never trust:** Platform memory (Claude memories, ChatGPT memory)
**Always read:** `00-system/state/current-state.md` at session start
**Session end:** Always output CONTEXT UPDATE block → commit to GitHub

## Rules

1. All state lives in GitHub, not in AI platform memory
2. Session start = fetch repo state first, then proceed
3. Session end = CONTEXT UPDATE block + commit all new files
4. Every 5 sessions = compress snapshots to `compressed-memory/`
5. CLAUDE.md = entry point for all AIs (loaded by Claude Code automatically)

## Multi-AI Handoff

Each AI has its own handoff file in `AI-HANDOFF/`:
- `AI-HANDOFF/claude.md` = Claude-specific instructions
- `AI-HANDOFF/chatgpt.md` = ChatGPT-specific instructions
- `AI-HANDOFF/gemini.md` = Gemini-specific instructions

Any AI can pick up where another left off by reading repo state.

## Rationale

Platform memory is unreliable, session-scoped, and non-transferable.
GitHub is durable, version-controlled, and readable by any AI.
This OS is designed for multi-AI collaboration — SSOT must be platform-agnostic.
