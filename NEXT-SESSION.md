# NEXT-SESSION.md — AgenticAI Learning OS
<!-- ONE FILE = FULL CONTEXT. Load this at start of every Claude.AI session. -->
<!-- Raw URL: https://raw.githubusercontent.com/pankildesai1988/AgenticAI/main/NEXT-SESSION.md -->
<!-- ⚠️ Always committed before session ends. Never trust platform memory. GitHub = SSOT. -->

---

## SESSION RESUME POINT
STATE_VERSION=v11
GENERATED=2026-06-10
GENERATED_BY=Claude (claude.ai chat, caveman/ultra mode)
CURRENT_PHASE=P02
CURRENT_TOPIC=T2 — Chunking Strategies (text, table, image, bbox)
PHASE_STATUS=IN_PROGRESS
CUT_POINT=NONE — T1 complete. Begin P02-T2 fresh.
NEXT_STEP=Start P02-T2 Chunking Strategies. Ask: "Pull up a real chunk from the Keysight PDF that got cut badly. We fix chunking on YOUR data." Fixed 600-char chunker cuts mid-sentence; page-number package pending — both are T2 entry material.
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
11. Consultant cards: PNG per topic + phase rollup (ADR-0009, master prompt v3.0 STEP 3b)

---

## WHAT PANKIL KNOWS (cumulative)
- P00: AI Foundation ✅ (foundation map, tokens/RAG, attention, API cost, agent mental models)
- P01: Prompt Engineering ✅ (anatomy, zero/few/CoT, system prompts, ArNir production, eval loop)
- P02-T1: Vector DB Architecture ✅ (exact/HNSW/IVFFlat, m/ef_construction/ef_search,
  isolate-the-layer diagnostic, operator-class bug, 7KB RAM math, pgvector ceiling ~10-50M,
  2026 vendor map: Qdrant=filtering, Pinecone=zero-ops-no-tuning, Milvus=billions)
- P02-T2 Chunking: NOT STARTED ← NEXT

Do NOT re-explain: RAG ✅, tokens ✅, prompt anatomy ✅, temperature ✅, system prompt 5-part ✅,
LLM-as-Judge ✅, HITL ✅, HNSW knobs ✅, ef_search-first debug order ✅, capacity math ✅

---

## ACTIVE PROJECTS
- ArNir: enterprise AI platform (.NET Core net9, pgvector, RAG, OpenAI/Claude/Gemini)
  SHIPPED 43f7dc7: 3-layer config (DB→appsettings→constants), HNSW index (cosine_ops,
  m=16, ef_con=64), VectorDbContextFactory, template placeholder bug fixed
  ({retrievedChunks} single-brace → context never injected — root cause of "Not found")
  PENDING: page-number change package (RagPageContent/Pages/PageNumber/per-page chunking),
  verify keyword Score 0.75 + hybrid 0.8/0.2 values applied, bbox=null for image/table chunks
- UpworkAgent OS: hybrid .NET/Python agentic freelance automation
  PENDING: 1 real winning proposal as few-shot | 7 Python fixes to _draft_with_claude
- Learning OS: P00 ✅ P01 ✅ P02 20% | mind maps 13 PNGs | consultant cards 1 PNG (NEW: ADR-0009)

---

## CURRENT PHASE CONTEXT
Phase: P02 — RAG Deep Dive
Entry: pgvector + HNSW live in ArNir. T1 grounded in real production deploy.
Topics:
  T1: Vector DB architecture ✅ DONE
  T2: Chunking strategies (text, table, image, bbox) ← NEXT
  T3: Embedding model selection + comparison
  T4: Hybrid search (semantic + keyword BM25) — note: ArNir hybrid merge already
      reviewed in T1 session (Score 1.0 bug); T4 deepens BM25 theory
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
1. Run master-session-end-prompt.md v3.0 (STEP 1-9 incl. 3a mindmap + 3b consultant card)
2. Announce: "Session end. Copy the NEXT-SESSION.md block below. Commit via Claude Code."
3. List all resource files + PNG files generated this session (pending git commit)
4. Commit format: `feat(P[XX]): [what was done]`
5. Mind map commit: separate → `chore(mindmap): P[XX]-T[NN] visual`
6. Consultant card commit: separate → `chore(card): P[XX]-T[NN] consultant card`
7. DO NOT end session without completing this block
8. Phase complete → collapse WHAT PANKIL KNOWS to 1 summary line. Goal: ≤ 150L forever.
