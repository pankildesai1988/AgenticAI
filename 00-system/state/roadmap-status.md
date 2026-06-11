# Roadmap Status
<!-- Max 150 lines. Update each phase completion. -->

## Phase Overview

| Phase | Name | Status | Progress | Completed |
|-------|------|--------|----------|-----------|
| P00 | AI Foundation | ✅ COMPLETE | 100% | 2026-05-25 |
| P01 | Prompt Engineering | ✅ COMPLETE | 100% | 2026-05-30 |
| P02 | RAG Deep Dive | 🔄 IN_PROGRESS | 20% (T1/5) | - |
| P03 | Agentic Patterns | ⏳ Pending | 0% | - |
| P04 | Multi-Agent Systems | ⏳ Pending | 0% | - |
| P05 | Tool Use & MCP | ⏳ Pending | 0% | - |
| P06 | Memory Systems | ⏳ Pending | 0% | - |
| P07 | Production AI | ⏳ Pending | 0% | - |
| P08 | Consulting Playbook | ⏳ Pending | 0% | - |
| P09 | Capstone Projects | ⏳ Pending | 0% | - |

**Overall: ~24% (P00 + P01 complete, P02 at T1/5)**

---

## P00 — AI Foundation ✅ COMPLETE (2026-05-25)
- P00: AI Foundation ✅ (foundation map, tokens/RAG, attention, API cost, agent mental models)
- Mind maps: p00-topic-01..05 + phase ✅ | Consultant cards: T1-T5 + phase ✅ (backfilled 2026-06-11)

---

## P01 — Prompt Engineering ✅ COMPLETE (2026-05-30)
- P01: Prompt Engineering ✅ (anatomy, zero/few/CoT, system prompts, ArNir production, eval loop)
- Mind maps: p01-topic-01..05 + phase ✅ | Consultant cards: T1-T5 + phase ✅ (backfilled 2026-06-11)
- Key outputs: UpworkAgent proposal prompt v2, job scoring CoT+few-shot,
  ArNir 5-part system prompt + healthcare demo shipped, eval dashboard, ADR-0008

---

## P02 — RAG Deep Dive 🔄 IN_PROGRESS

**Topics:**
- T1: Vector DB architecture (pgvector deep dive) ✅ DONE 2026-06-10
- T2: Chunking strategies (text, table, image, bbox) ← NEXT
- T3: Embedding model selection + comparison
- T4: Hybrid search (semantic + keyword BM25)
- T5: Reranking + RAG evaluation metrics

**T1 outputs:**
- ArNir shipped (43f7dc7): 3-layer config system, HNSW index
  (vector_cosine_ops, m=16, ef_construction=64), VectorDbContextFactory,
  prompt template placeholder root cause fixed
- ADR-0009: Consultant Card protocol (new visual artifact type)
- master-session-end-prompt.md v3.0 (STEP 3b cards)
- Artifacts: p02-topic-01-mindmap.png + p02-topic-01-consultant-card.png
- Knowledge locked: exact/HNSW/IVFFlat, knob costs, isolate-the-layer
  diagnostic, operator-class bug, 7KB RAM math, migration triggers,
  2026 vendor landscape

---

## Mutation Log

| Date | Mutation | Reason |
|------|----------|--------|
| 2026-06-10 | ADR-0009 + consultant cards added to session-end protocol (v3.0) | T1: need judgment-tool artifact beyond memory-aid mind maps |
| 2026-06-10 | P02-T4 note: ArNir hybrid merge already reviewed in T1 (Score 1.0 bug) | T4 will deepen BM25 theory, not re-discover the bug |
| 2026-06-11 | Consultant cards backfilled P00+P01 (12) · viewport rule 1200=body width (ADR-0009) | Right-edge dead strip on all full_page PNGs |

---

## Repo Structure Status

| Folder | Status | Notes |
|--------|--------|-------|
| 00-system/ | ✅ Active | ADRs 0001-0009 |
| 01-memory/ | ✅ Active | Session snapshots |
| 02-learning/ | ✅ Active | P00+P01 done, P02 active; mindmaps/ + consultant-cards/ |
| 03-prompts/ | ✅ Active | master-session-end-prompt v3.0, proposal prompt v2 |
| 07-projects/ | ✅ Active | arnir-status.md |
| AI-HANDOFF/ | ✅ Active | Claude, ChatGPT, Gemini, Perplexity |

---

## Learning Style Rules (Permanent)
- Caveman/ultra mode = default
- .NET analogies OK
- Practical > theory always
- Consultant framing at every topic
- Client-ready language in use cases
- Generate resource file + mind map PNG + consultant card PNG immediately after each topic
