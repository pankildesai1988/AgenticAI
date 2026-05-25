# CLAUDE.md — AgenticAI Learning OS
<!-- Auto-loaded by Claude Code. MAX 200 lines. -->
<!-- Manual use: paste into claude.ai at session start -->
<!-- Repo: https://github.com/pankildesai1988/AgenticAI (public) -->

## ⚡ SESSION START — DO THIS FIRST (Every Single Session)

```
STEP 1: Read repo state (Claude.ai = web_fetch, Claude Code = file read)
  → web_fetch: https://github.com/pankildesai1988/AgenticAI/blob/main/CLAUDE.md
  → web_fetch: https://github.com/pankildesai1988/AgenticAI/blob/main/00-system/state/current-state.md

STEP 2: Check ADRs for any new decisions since last session
  → web_fetch: https://github.com/pankildesai1988/AgenticAI/tree/main/00-system/decisions/

STEP 3: Apply ALL ADR rules before doing anything
  → ADR-001: [check repo]
  → ADR-002: [check repo]
  → ADR-003: One resource file per topic, web-fetched, generated AFTER topic done

STEP 4: Announce to user:
  "Loaded state v[X]. Current phase: [phase]. Last session: [date]. 
   Resuming from: [NEXT_ACTION]. Any corrections?"
```

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
STATE_VERSION=v3
LAST_UPDATED=2026-05-25
LAST_AI=Claude
CURRENT_PHASE=P00
PHASE_STATUS=In Progress
NEXT_ACTION=Commit 4 files → setup Claude Code → start Topic 4 (API call)
BLOCKER=None
PROGRESS=30%
COMPLETED=
- T1: AI/ML/DL/GenAI map ✅
- T2: Tokens/Embeddings/Context/RAG ✅
- T3: Attention mechanism + RAG+Attention combo ✅
- T4: First API Call — Parameters, Cost & Router Pattern ✅
- CLAUDE.md updated with session sync rules ✅
- ADR-003 resource format decision ✅
PENDING_COMMITS=
- CLAUDE.md (replace existing)
- 02-learning/phase-P00/resources/p00-topic-01-resources.md
- 02-learning/phase-P00/resources/p00-topic-02-resources.md
- 02-learning/phase-P00/resources/p00-topic-03-resources.md
- 02-learning/phase-P00/resources/p00-topic-04-resources.md
- 00-system/decisions/ADR-003-resource-format.md
---END---
```

## Decisions Log
See 00-system/decisions/ for all ADRs.
ADR-003: Resource file format and generation rules (2026-05-25)
