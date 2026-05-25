# ADR-0004: GitHub as Single Source of Truth (SSOT)

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
**Session start:** Load NEXT-SESSION.md (see ADR-0006)
**Session end:** Always generate updated NEXT-SESSION.md block → commit to GitHub

## Rules

1. All state lives in GitHub, not in AI platform memory
2. Session start = fetch NEXT-SESSION.md first (single file, all context)
3. Session end = generate NEXT-SESSION.md block + commit all new files
4. Every 5 sessions = compress snapshots to `compressed-memory/`
5. CLAUDE.md = entry point for Claude Code (auto-loaded)

## Multi-AI Handoff

Each AI has its own handoff file in `AI-HANDOFF/`:
- `AI-HANDOFF/chatgpt.md` = ChatGPT-specific instructions
- `AI-HANDOFF/gemini.md` = Gemini-specific instructions
- `AI-HANDOFF/perplexity.md` = Perplexity research-only instructions

All platform files reference NEXT-SESSION.md as the context source.
Any AI can pick up where another left off by reading NEXT-SESSION.md.

## Rationale

Platform memory is unreliable, session-scoped, and non-transferable.
GitHub is durable, version-controlled, and readable by any AI.
This OS is designed for multi-AI collaboration — SSOT must be platform-agnostic.
