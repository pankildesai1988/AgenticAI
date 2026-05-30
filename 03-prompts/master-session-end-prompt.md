# Master Session-End Prompt
VERSION=2.0
CREATED=2026-05-27
UPDATED=2026-05-30
PHASE_VALIDATED=P01-T5

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

  STEP 3a: Generate TOPIC mind map PNG (ADR-0008)
          a. Build HTML mind map in memory (intermediate only — never commit HTML)
          b. Run playwright render → PNG
          c. Output path: 02-learning/phase-P[XX]/mindmaps/p[XX]-topic-[NN]-mindmap.png
          d. Mind map rules: see ADR-0008 (colorful cards, NOT flow diagram,
             acronym + analogies + Do/Avoid + Memory Palace, brand spec exact)
          e. If phase is COMPLETE → ALSO generate PHASE mind map PNG:
             Path: 02-learning/phase-P[XX]/mindmaps/p[XX]-phase-mindmap.png
             Phase map = all topics of phase combined into one visual summary

  STEP 4: Generate session snapshot
          Path: 01-memory/sessions/YYYY-MM-DD-P[XX]-T[NN].md
  STEP 5: Generate updated NEXT-SESSION.md (all fields updated)
  STEP 6: Generate updated current-state.md
  STEP 7: Generate updated roadmap-status.md (only if phase status changed)

  STEP 7a: If phase COMPLETE → verify both PNGs committed:
           - All topic mindmaps: p[XX]-topic-01 through p[XX]-topic-[NN]
           - Phase mindmap: p[XX]-phase-mindmap.png
           List any missing PNGs → generate retroactively before committing

  STEP 8: List all files generated + git commit commands
  STEP 9: Download new generated files (PNGs + markdown)

Format: Markdown files in fenced blocks with filename as header.
        PNG files via playwright render (Claude Code).
        No plain text outside file blocks.

Constraints:
- Follow ADR-0005: web-fetch links before resource file generation
- Follow ADR-0006: NEXT-SESSION.md ≤ 150L
- Follow ADR-0008: PNG only (never commit HTML mind maps)
- Follow token-limits.md: current-state.md ≤ 100L
- NEXT_STEP must be specific: first action of next topic
- CUT_POINT = NONE if topic ended cleanly
- Git ops reminder: Claude Code only, never Claude.ai chat
- Commit format: feat(P[XX]): [what was done]
- Mind map commit: always separate commit → chore(mindmap): P[XX]-T[NN] visual

---

## Mind Map Design Rules (ADR-0008 summary — apply to every map)

STYLE:       Colorful card-based mind map. NEVER a flow diagram.
AUDIENCE:    Anyone — technical or non-technical language.
STRUCTURE:   Acronym/mnemonic hero · 6 topic cards · Analogies · Stack/Layers · Do/Avoid · Memory Palace
BRAND:       accelvel SVG logo (exact spec) top-left · Tagline underneath · Pankil Desai top-right
FOOTER:      Dark #1C1A17 bar · phase+topic label · accelvel.com credit
FONTS:       Fredoka One (headings) · Nunito (body) · Outfit (brand elements)
NUMBERS:     All scores/metrics = generic examples (not live production data)
CANVAS:      width=1200px · full_page=True · viewport 1280×900
OUTPUT:      PNG only. HTML is temp/discarded.

LOGO SVG (exact — never alter):
  Outer A: #E8622A, SW=8, square linecap, clipPath y=-2..75
  Inner A: #1C1A17 (light bg) / #FAF3EE (dark bg), SW=8, square, clipPath y=37.2..75
  viewBox: "2 0 72 75"
  Wordmark: accel(#E8622A) + vel(#1C1A17), Outfit 600, letter-spacing -0.5px
  Tagline: "From idea to impact — faster." (#E8622A on "— faster.")
  Gap: 14px between icon and wordmark

---

## Version History
| Version | Date | Change | Phase |
|---------|------|--------|-------|
| 1.0 | 2026-05-27 | Initial | P01-T1 |
| 2.0 | 2026-05-30 | Added STEP 3a + STEP 7a: topic + phase PNG mindmaps (ADR-0008) | P01-T5 |
