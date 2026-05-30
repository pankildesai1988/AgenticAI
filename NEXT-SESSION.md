# NEXT-SESSION.md — AgenticAI Learning OS
<!-- ONE FILE = FULL CONTEXT. Load this at start of every Claude.AI session. -->
<!-- Raw URL: https://raw.githubusercontent.com/pankildesai1988/AgenticAI/main/NEXT-SESSION.md -->
<!-- ⚠️ Always committed before session ends. Never trust platform memory. GitHub = SSOT. -->

---

## SESSION RESUME POINT
STATE_VERSION=v10
GENERATED=2026-05-30
GENERATED_BY=Claude (claude.ai chat, caveman/ultra mode)
CURRENT_PHASE=P02
CURRENT_TOPIC=T1 — Vector DB Architecture (pgvector deep dive)
PHASE_STATUS=NOT_STARTED
CUT_POINT=NONE — P01 complete. Begin P02 fresh.
NEXT_STEP=Start P02-T1. Ask: "Show me your current ArNir chunking code. What does a chunk look like? How big? What metadata?" Ground in existing code before teaching theory.
BLOCKER=None

---

## IDENTITY
Pankil = 15yr .NET dev → Agentic AI Consultant.
Mode: Caveman/ultra (compressed, no fluff). .NET analogies OK. Consultant angle = required on every topic.
Practical before theory. Cost/ROI math = always good hook. Numbers → understanding.
Restaurant + ArNir analogies = Pankil connects fastest.
Socratic check: ask Pankil to apply concept before moving on.

---

## RULES (non-negotiable, apply every session)
1. Never trust platform memory → GitHub = SSOT, always
2. Session end → generate full NEXT-SESSION.md block → user commits to GitHub
3. Resource files: generate ONLY after topic done, web-fetch fresh links first
4. One resource file per topic: `02-learning/phase-P[XX]/resources/p[XX]-topic-[NN]-resources.md`
5. Git ops → Claude Code only (never Claude.AI/chat)
6. CLAUDE.md changes → push immediately, don't wait for session end
7. Token limits: current-state.md ≤ 100L | roadmap ≤ 150L | phase files ≤ 400L
8. Every 5 sessions → compress snapshots → compressed-memory/
9. ADR format: ADR-0001 through ADR-NNNN (4-digit, sequential)
10. Mind maps: PNG only via playwright — HTML never committed (ADR-0008)

---

## WHAT PANKIL KNOWS (cumulative)
- P00: AI Foundation ✅ (foundation map, tokens/RAG, attention, API cost, agent mental models)
- P01: Prompt Engineering ✅ (anatomy, zero/few/CoT, system prompts, ArNir production, eval loop)
- RAG Deep Dive: NOT STARTED → P02

Do NOT re-explain: RAG ✅, tokens ✅, chatbot vs agent ✅, prompt anatomy ✅, zero/few/CoT ✅,
temperature ✅, system prompt 5-part ✅, LLM-as-Judge ✅, HITL ✅, feedback loop ✅

---

## ACTIVE PROJECTS
- ArNir: enterprise AI platform (.NET Core net9, pgvector, RAG, OpenAI/Claude/Gemini)
  SHIPPED: PDF inline viewer + source highlight + confidence badge (healthcare demo ✅)
  SHIPPED: Evaluation dashboard (R+F scores, daily trends, reasoning per query) ✅
  Next: ecommerce + finance demos OR S3/Blob PDF storage
  Project note: `07-projects/arnir/arnir-status.md`
- UpworkAgent OS: hybrid .NET/Python agentic freelance automation
  Proposal prompt v2: 7 fixes applied ✅ | Job scoring: CoT + few-shot ✅
  PENDING: 1 real winning proposal as few-shot example
  PENDING: apply 7 Python fixes to _draft_with_claude
- This Learning OS: P00 ✅ P01 ✅ | 12 mind map PNGs committed

---

## CURRENT PHASE CONTEXT
Phase: P02 — RAG Deep Dive
Entry: pgvector + bbox chunking already in ArNir. Optimize + extend existing.
Topics:
  T1: Vector DB architecture (pgvector deep dive) ← NEXT
  T2: Chunking strategies (text, table, image, bbox)
  T3: Embedding model selection + comparison
  T4: Hybrid search (semantic + keyword BM25)
  T5: Reranking + RAG evaluation metrics

---

## SESSION START SCRIPT (AI must say this after loading)
"Loaded v[X]. Phase P[XX]. Topic T[NN]: [name].
Resuming from: [CUT_POINT field above].
Rules loaded: Caveman/ultra, GitHub SSOT, no platform memory.
[NEXT_STEP field above]
Any corrections before we start?"

---

## CUT POINT PROTOCOL
Fill CUT_POINT when session breaks mid-topic (not at clean topic end).
Format: `P[XX]-T[NN]: Covered [A] and [B]. NOT YET covered [C]. Next: [first thing to do].`
If CUT_POINT=NONE → start next topic T(N+1) fresh.

---

## SESSION END PROCEDURE (AI must do this — no exceptions)
1. Generate FULL updated NEXT-SESSION.md content (all fields updated)
2. Announce: "Session end. Copy the NEXT-SESSION.md block below. Commit via Claude Code."
3. List all resource files + PNG files generated this session (pending git commit)
4. Commit message format: `feat(P[XX]): [what was done]`
5. Mind map commit: separate → `chore(mindmap): P[XX]-T[NN] visual`
6. DO NOT end session without completing this block
7. Phase complete → collapse WHAT PANKIL KNOWS:
   Replace topic lines with 1 summary: `P[XX]: [Phase Name] ✅ ([keyword, keyword, keyword])`
   Goal: NEXT-SESSION.md stays ≤ 150L forever.
