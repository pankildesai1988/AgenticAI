# CLAUDE.md — AgenticAI Learning OS
<!-- Auto-loaded by Claude Code. MAX 200 lines. -->
<!-- Manual use: paste into claude.ai at session start -->
<!-- Repo: https://github.com/pankildesai1988/AgenticAI (public) -->

## ⚡ SESSION START — ONE STEP

```
web_fetch: https://raw.githubusercontent.com/pankildesai1988/AgenticAI/main/NEXT-SESSION.md
→ Everything needed is in that file. Read it. Announce resume point. Begin.

Announce: "Loaded v[X]. Phase [P]. Topic [T]. Resuming from: [CUT_POINT]. Any corrections?"
```

Note: NEXT-SESSION.md contains identity, rules, phase context, resume point, and session scripts.
If web_fetch fails → tell user immediately, paste NEXT-SESSION.md content manually.

## Identity
Pankil = 15yr .NET dev → Agentic AI Consultant.
Teach: practical > theory. .NET analogies OK. Caveman/ultra mode.
Profile: 01-memory/consultant-profile/identity.md

## Tool Selection Rule (Claude.ai vs Claude Code)
```
Claude.ai (chat):
  → Learning, concepts, Q&A, mental models, resource generation, mind map HTML

Claude Code (terminal):
  → Git read/write, file commits, running code, playwright PNG render
  → ALWAYS use Claude Code for git ops — never rely on chat for repo writes
  → ALWAYS use Claude Code for playwright: python3 mindmap render script

Rule: If task needs git or PNG render → stop → switch to Claude Code
```

## Resource File Rules (ADR-0005)
- Generate ONLY after topic completed in session
- One file per topic: `02-learning/phase-P[XX]/resources/p[XX]-topic-[NN]-resources.md`
- Always web_fetch for fresh links before generating
- Include: Blog, YouTube Video, YouTube Short, Substack, Real Business Use Cases
- Each entry: Title + Link + 4-bullet summary
- Non-tech language in use cases (client-ready)

## Mind Map Rules (ADR-0008)
- Generate AFTER resource file, BEFORE session snapshot
- Topic map: `02-learning/phase-P[XX]/mindmaps/p[XX]-topic-[NN]-mindmap.png`
- Phase map:  `02-learning/phase-P[XX]/mindmaps/p[XX]-phase-mindmap.png`
- HTML = intermediate only (temp file, never commit)
- PNG = final output (commit separately: chore(mindmap): ...)
- Style: colorful cards, NOT flow diagram, audience = anyone
- Must have: acronym hero + 6 cards + analogies + Do/Avoid + Memory Palace
- Brand: exact accelvel logo SVG + tagline + Pankil Desai credit
- Render: playwright chromium, 1280px viewport, full_page=True
- See full spec: 00-system/decisions/ADR-0008-visual-mindmap.md

## After Each Topic (Checklist)
```
✅ Topic learning done
✅ Generate resource file (web_fetch first)
✅ Generate topic mind map PNG (Claude Code playwright render)
✅ Announce: "Topic X done. Resource file + PNG ready. Commit when ready."
✅ Update CONTEXT UPDATE block
```

## After Each Session (Rules)
```
✅ Output CONTEXT UPDATE block
✅ List ALL resource files + PNG files pending git commit
✅ Remind: "Use Claude Code to commit + render PNGs"
✅ git commit format: feat(P[XX]): [what was done]
✅ mind map commit: chore(mindmap): P[XX]-T[NN] visual
```

## Rules (Quick)
- current-state.md ≤ 100L | roadmap ≤ 150L | phase files ≤ 400L
- Session end → CONTEXT UPDATE block → git commit via Claude Code
- Never trust platform memory → GitHub = SSOT
- Every 5 sessions → compress snapshots → compressed-memory/
- Full rules: 00-system/rules/
- CLAUDE.md changes → always push immediately

## Repo Read (Claude.ai Chat Mode)
```
Read any file:
  web_fetch: https://github.com/pankildesai1988/AgenticAI/blob/main/[path]
Read raw:
  web_fetch: https://raw.githubusercontent.com/pankildesai1988/AgenticAI/main/[path]
If web_fetch blocked → tell user immediately, don't silently fail
```

## Decisions Log
See 00-system/decisions/ for all ADRs.
ADR-0001: Repo folder structure (2026-05-24)
ADR-0002: Multi-AI strategy (2026-05-24)
ADR-0003: Learning style + teaching protocol (2026-05-25)
ADR-0004: GitHub as SSOT (2026-05-25)
ADR-0005: Resource file format (2026-05-24)
ADR-0006: Single-file session handoff / NEXT-SESSION.md (2026-05-25)
ADR-0007: Master prompt strategy + 03-prompts/ folder (2026-05-27)
ADR-0008: Visual mind map PNG generation protocol (2026-05-30)
