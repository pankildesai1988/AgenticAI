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
  → Learning, concepts, Q&A, mental models, resource generation

Claude Code (terminal):
  → Git read/write, file commits, running code, ArNir/UpworkAgent for referance builds
  → ALWAYS use Claude Code for git ops — never rely on chat for repo writes

Rule: If task needs git → stop → switch to Claude Code
```

## Resource File Rules (ADR-003)
- Generate ONLY after topic completed in session
- One file per topic: `02-learning/phase-P[XX]/resources/p[XX]-topic-[NN]-resources.md`
- Always web_fetch for fresh links before generating
- Include: Blog, YouTube Video, YouTube Short, Substack, Real Business Use Cases
- Each entry: Title + Link + 4-bullet summary
- Non-tech language in use cases (client-ready)
- Generate T2 + T3 files if missed — never skip

## After Each Topic (Checklist)
```
✅ Topic learning done
✅ Generate resource file (web_fetch first)
✅ Announce: "Topic X done. Resource file ready. Commit when ready."
✅ Update CONTEXT UPDATE block
```

## After Each Session (Rules)
```
✅ Output CONTEXT UPDATE block (see format below)  
✅ List ALL resource files pending git commit
✅ Remind: "Use Claude Code to commit these files"
✅ git commit format: "feat(P[XX]): [what was done]"
```

## Rules (Quick)
- current-state.md ≤ 100L | roadmap ≤ 150L | phase files ≤ 400L
- Session end → CONTEXT UPDATE block → git commit via Claude Code
- Never trust platform memory → GitHub = SSOT
- Every 5 sessions → compress snapshots → compressed-memory/
- Full rules: 00-system/rules/
- CLAUDE.md changes → always push immediately, don't wait for session end

## Repo Read (Claude.ai Chat Mode)
```
Claude.ai CANNOT push to git directly.
Claude.ai CAN read public repo via web_fetch.

Read any file:
  web_fetch: https://github.com/pankildesai1988/AgenticAI/blob/main/[path]

Read folder tree:
  web_fetch: https://github.com/pankildesai1988/AgenticAI/tree/main/[path]

If web_fetch blocked → tell user immediately, don't silently fail
```

## Session End Output
```
---CONTEXT UPDATE---
STATE_VERSION=v5
LAST_UPDATED=2026-05-25
LAST_AI=Claude
CURRENT_PHASE=P00
PHASE_STATUS=COMPLETE ✅
NEXT_ACTION=Commit all 7 files via GitHub Desktop → start P01 next session
BLOCKER=None
PROGRESS=100% P00 / 10% overall
COMPLETED=
- T1-T5 all topics + resource files ✅
- CLAUDE.md session sync rules ✅
- ADR-003 resource format decision ✅
- ReAct + Planner+Tools+Memory mental model ✅
- Semantic Kernel identified for ArNir upgrade path ✅
PENDING_COMMITS=
- CLAUDE.md
- ADR-003-resource-format.md
- p00-topic-01 through p00-topic-05 resource files (5 files)
---END---
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
