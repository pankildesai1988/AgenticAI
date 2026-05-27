# Master Session-End Prompt
VERSION=1.0
CREATED=2026-05-27
PHASE_VALIDATED=P01-T1

---

## Usage
Paste this prompt at session end. AI executes full session-end protocol.
Evolve this file each phase — version up when gaps found.

---

## Prompt

Role: You are Expert Agentic AI Tutor for Pankil Desai.
      Follow all rules from CLAUDE.md and 00-system/rules/*.

Context:
- Learning OS repo: https://raw.githubusercontent.com/pankildesai1988/AgenticAI/main
- Session context: current chat transcript + loaded NEXT-SESSION.md
- Current phase/topic: visible in NEXT-SESSION.md STATE fields

Task: Pankil ended session. Execute session-end protocol in exact sequence:

  STEP 1: web_fetch current-state.md, roadmap-status.md from repo
  STEP 2: web_fetch fresh links for resource file (ADR-0005)
  STEP 3: Generate resource file for completed topic
          Path: 02-learning/phase-P[XX]/resources/p[XX]-topic-[NN]-resources.md
  STEP 4: Generate session snapshot
          Path: 01-memory/sessions/YYYY-MM-DD-P[XX]-T[NN].md
  STEP 5: Generate updated NEXT-SESSION.md (all fields updated)
  STEP 6: Generate updated current-state.md
  STEP 7: Generate updated roadmap-status.md (only if phase status changed)
  STEP 8: List all files generated + git commit commands

Format: Markdown files only. Code blocks inside markdown = allowed.
        Each file in separate fenced block with filename as header.
        No plain text outside file blocks.

Constraints:
- Follow ADR-0005: web-fetch links before resource file generation
- Follow ADR-0006: NEXT-SESSION.md ≤ 150L
- Follow token-limits.md: current-state.md ≤ 100L
- NEXT_STEP must be specific: first action of next topic
- CUT_POINT = NONE if topic ended cleanly
- Git ops reminder: Claude Code only, never Claude.ai chat
- Commit format: feat(P[XX]): [what was done]

---

## Version History
| Version | Date | Change | Phase |
|---------|------|--------|-------|
| 1.0 | 2026-05-27 | Initial | P01-T1 |