# ADR-0009: Consultant Card Generation Protocol

DATE=2026-06-10
STATUS=ACCEPTED
DECIDED_BY=Pankil + Claude

---

## Context

ADR-0008 mind maps = memory aids (anyone-audience, playful style).
Gap identified during P02-T1: no artifact captures **consultant judgment** —
tool comparisons, decision tables, cost trade-offs, and memorizable client
pitches. Learning a topic ≠ being able to consult on it. Need a second
visual artifact type optimized for decision-making and client conversations.

## Decision

**After every topic AND after every phase completion:**
Generate a branded **consultant card PNG** in addition to the mind map PNG.

**Two artifacts, two jobs (locked):**
| Artifact | Job | Audience | Style |
|----------|-----|----------|-------|
| Mind map (ADR-0008) | Memory aid | Anyone | Fredoka/Nunito, playful cards |
| Consultant card (this ADR) | Judgment tool | Pankil as consultant | Outfit-only, strict brand |

**Tool chain:** HTML → Playwright (chromium) → PNG
- HTML is intermediate only (not committed, not shared)
- PNG is the final deliverable — committed to repo + shareable

**Storage path:**
- Topic card: `02-learning/phase-P[XX]/consultant-cards/p[XX]-topic-[NN]-consultant-card.png`
- Phase card: `02-learning/phase-P[XX]/consultant-cards/p[XX]-phase-consultant-card.png`

**Trigger (session-end sequence, master prompt v3.0):**
- Topic end → STEP 3b, after mind map (3a), before snapshot (4)
- Phase end → ALSO generate phase rollup card; STEP 7a verifies all card PNGs

**Phase card = rollup:** all topic decision RULES + all pitches of the
phase + phase-level memory palace. Same brand spec.

---

## Required Sections (in order, non-negotiable)

1. **HERO** — dark #1C1A17 block, phase+topic label, title with ember
   accent, mnemonic/acronym line
2. **CONCEPT MAP** — 3-4 nodes comparing the topic's tools/approaches,
   recommended option highlighted (ember border + ★)
3. **DECISION TABLE** — factor rows × tool columns + "Realistic Example"
   column. Color-code: green=good, amber=mid, red=bad. Include the topic's
   invisible-bug row if one exists. One RULE line under the table.
4. **KNOBS/COSTS** — tunable parameters as cards: what it does, .NET
   analogy, cost badge (BUILD-TIME=red, QUERY-TIME/FREE=green)
5. **DEBUG ORDER** — numbered steps cheapest-first with badges:
   FREE → DIAGNOSTIC → escalation → LAST RESORT *(only if topic has a debug flow)*
6. **CAPACITY/MATH** — scale table + stay/leave decision flow with real
   $ numbers *(only if topic has scale economics)*
7. **PITCHES** — 2-3 memorizable pitch cards. Each MUST have:
   - USE WHEN trigger line (uppercase, ember)
   - Quote with KEY WORDS highlighted (ember-glow background)
   - Win line (green): why this pitch lands / what it earns
8. **MEMORY PALACE** — dark footer block, 3 columns:
   analogy story · .NET anchors · Do/Avoid

Sections 5 and 6 are conditional; 1-4, 7, 8 are mandatory on every card.

---

## Brand Rules (non-negotiable)

- Logo: exact accelvel SVG spec (ADR-0008 logo spec) — top-left
- Tagline: "From idea to impact — faster." under logo
- "Pankil Desai · Agentic AI Consultant" — top-right
- Footer bar: dark `#1C1A17`, "P[XX] · [Phase] · T[NN] · [Topic]" left,
  "Knowledge card · accelvel.com" right
- **Font: Outfit ONLY** (300-800) — no Fredoka, no Nunito (that's mind maps)
- Colors: Ember #E8622A · Charcoal #1C1A17 · WarmBG #FAF3EE ·
  WarmWhite #FDFBF8 · semantic green #2E7D4F / red #B3402A /
  blue #2A5FA8 / amber #B07818
- Never pure #ffffff or #000000
- Full brand kit reference: accelvel repo CLAUDE.md (colors, radii, shadows)
- Canvas: width=1200px · **viewport 1200×900 (MUST equal body width —
  wider viewport leaves a dead strip on the right edge of full-page PNG)** ·
  full_page=True
- Numbers: real consulting numbers OK ($/mo, ms, GB) as generic examples —
  never live client data

---

## Rationale

- Mind map answers "do I remember this?" — card answers "can I bill for this?"
- Decision tables + pitches = direct reuse in client calls, proposals, audits
- USE WHEN triggers turn pitches into deployable scripts, not trivia
- PNG = shareable on LinkedIn/WhatsApp = portfolio + lead-gen asset
- Same toolchain as ADR-0008 = zero new infrastructure

## Consequences

- Session end adds STEP 3b (master-session-end-prompt.md → v3.0)
- New folder per phase: `02-learning/phase-P[XX]/consultant-cards/`
- Phase completion now verifies 4 PNG sets (mindmaps + cards × topic + phase)
- Separate commit convention: `chore(card): P[XX]-T[NN] consultant card`
- HTML intermediates: NOT committed (generated and discarded)
- Claude Code runs the playwright render command (same as ADR-0008)

## Render Command (Claude Code)
```bash
python3 -c "
from playwright.sync_api import sync_playwright
with sync_playwright() as p:
    b = p.chromium.launch()
    pg = b.new_page(viewport={'width':1200,'height':900})  # MUST match body width
    pg.goto('file:///home/claude/card_temp.html')
    pg.wait_for_timeout(2500)
    pg.screenshot(path='/path/to/p[XX]-topic-[NN]-consultant-card.png', full_page=True)
    b.close()
"
```
RULE (applies to ALL PNG artifacts incl. ADR-0008 mind maps):
viewport width == body width == 1200. A wider viewport (e.g. 1280)
adds an 80px dead strip on the right of every full_page screenshot.
Fixed 2026-06-11; all 13 existing cards re-rendered at 1200.

## First Artifact
`p02-topic-01-consultant-card.png` (Vector DB Architecture) — generated
2026-06-10, validated against this spec.
