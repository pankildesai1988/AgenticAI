# ADR-0008: Visual Mind Map Generation Protocol

DATE=2026-05-30
STATUS=ACCEPTED
DECIDED_BY=Pankil + Claude

---

## Context

Learning topics and phases need a shareable, long-lasting visual memory aid.
HTML files are not shareable. Screenshots vary. Need a repeatable, branded PNG output.
Reference style: colorful mind map (see CRAFT image reference), NOT a flow diagram.
Target audience: anyone — technical or non-technical.

## Decision

**After every topic AND after every phase completion:**
Generate a branded PNG mind map image as a permanent visual memory artifact.

**Tool chain:** HTML → Playwright (chromium) → PNG
- HTML is intermediate only (not committed, not shared)
- PNG is the final deliverable — committed to repo + shareable

**Storage path:**
- Topic map: `02-learning/phase-P[XX]/mindmaps/p[XX]-topic-[NN]-mindmap.png`
- Phase map:  `02-learning/phase-P[XX]/mindmaps/p[XX]-phase-mindmap.png`

**Trigger:**
- Topic end → generate topic PNG (after resource file, before NEXT-SESSION.md)
- Phase end → generate phase PNG (after all topic PNGs, before phase collapse)

**Brand rules (non-negotiable, apply to every map):**
- Logo: exact accelvel SVG spec (ADR-0008-logo-spec below) — top-left
- Tagline: "From idea to impact — faster." under logo
- "Pankil Desai · Agentic AI Consultant" — top-right
- Bottom bar: dark `#1C1A17` bg, phase + topic label, accelvel.com credit
- NO orbixnex.com, NO generic favicon, NO "Created by" text

**Design rules (non-negotiable):**
- Style: colorful card-based mind map — NOT a flow diagram
- Audience: anyone (technical or non-technical language)
- Fonts: Fredoka One (headings) + Nunito (body) + Outfit (brand)
- Must include: acronym/mnemonic, analogies, Do/Avoid, Memory Palace
- All numbers/scores = generic examples (not live data)
- Canvas width: 1200px, full-page height
- Output PNG: 1280px viewport, full_page=True

---

## Logo Spec (locked — never alter)

```svg
<svg viewBox="2 0 72 75" fill="none" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <clipPath id="co"><rect x="0" y="-2" width="80" height="77"/></clipPath>
    <clipPath id="ci"><rect x="0" y="37.2" width="80" height="38"/></clipPath>
  </defs>
  <g clip-path="url(#co)">
    <line x1="38" y1="0"    x2="6"    y2="75" stroke="#E8622A" stroke-width="8" stroke-linecap="square"/>
    <line x1="38" y1="0"    x2="70"   y2="75" stroke="#E8622A" stroke-width="8" stroke-linecap="square"/>
  </g>
  <g clip-path="url(#ci)">
    <line x1="38" y1="37.2" x2="21.9" y2="75" stroke="#1C1A17" stroke-width="8" stroke-linecap="square"/>
    <line x1="38" y1="37.2" x2="54.1" y2="75" stroke="#1C1A17" stroke-width="8" stroke-linecap="square"/>
  </g>
</svg>
```
Dark bg variant: inner color = `#FAF3EE`
Wordmark: `<accel>#E8622A</accel><vel>#1C1A17</vel>` · Outfit 600 · letter-spacing -0.5px

---

## Rationale

- PNG = universally shareable (WhatsApp, email, LinkedIn, print)
- Playwright = no external API, no cost, reproducible
- Branded = professional consulting asset
- Mind map style = works for non-technical audience
- Per-topic + per-phase = two levels of memory reinforcement

## Consequences

- Session end adds 2 steps: generate HTML → render PNG → commit PNG
- master-session-end-prompt.md updated to v2.0 (adds STEP 3a + STEP 7a)
- New folder per phase: `02-learning/phase-P[XX]/mindmaps/`
- HTML intermediate files: NOT committed (generated and discarded)
- Claude Code runs the playwright render command

## Render Command (Claude Code)
```bash
python3 -c "
from playwright.sync_api import sync_playwright
with sync_playwright() as p:
    b = p.chromium.launch()
    pg = b.new_page(viewport={'width':1280,'height':900})
    pg.goto('file:///home/claude/mindmap_temp.html')
    pg.wait_for_timeout(2000)
    pg.screenshot(path='/path/to/output.png', full_page=True)
    b.close()
"
```
