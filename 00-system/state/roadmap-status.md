# Roadmap Status
<!-- Max 150 lines. Update each phase completion. -->

## Phase Overview

| Phase | Name | Status | Progress | Completed |
|-------|------|--------|----------|-----------|
| P00 | AI Foundation | ✅ COMPLETE | 100% | 2026-05-25 |
| P01 | Prompt Engineering | 🔜 NEXT | 0% | - |
| P02 | RAG Deep Dive | ⏳ Pending | 0% | - |
| P03 | Agentic Patterns | ⏳ Pending | 0% | - |
| P04 | Multi-Agent Systems | ⏳ Pending | 0% | - |
| P05 | Tool Use & MCP | ⏳ Pending | 0% | - |
| P06 | Memory Systems | ⏳ Pending | 0% | - |
| P07 | Production AI | ⏳ Pending | 0% | - |
| P08 | Consulting Playbook | ⏳ Pending | 0% | - |
| P09 | Capstone Projects | ⏳ Pending | 0% | - |

**Overall: 10% (1/10 phases complete)**

---

## P00 — AI Foundation ✅ COMPLETE

**Topics completed:**
- T1: AI/ML/DL/GenAI map
- T2: Tokens → Embeddings → Context → RAG
- T3: Attention mechanism
- T4: API calls + parameters + cost math + Router Agent
- T5: Agent mental models + ReAct + Planner+Tools+Memory

**Resource files:** `02-learning/phase-P00/resources/` (5 files)
**Key outcome:** Can explain AI stack to clients + calculate ROI + design agent architecture

---

## P01 — Prompt Engineering 🔜 NEXT

**Topics to cover:**
- T1: Prompt anatomy (role, context, instruction, format)
- T2: Zero-shot vs few-shot vs chain-of-thought
- T3: System prompt design
- T4: Prompt patterns (ReAct, Tree of Thought, Self-ask)
- T5: Prompt optimization for cost + quality

**Entry condition:** P00 complete ✅
**Pankil's edge:** Uses prompts daily. Gap = WHY some work, others don't.

---

## P02 — RAG Deep Dive ⏳

**Topics planned:**
- Vector DB architecture (pgvector deep dive)
- Chunking strategies
- Embedding model selection
- Hybrid search (semantic + keyword)
- Reranking + evaluation

**Pankil's edge:** Already has pgvector in ArNir. Will optimize existing implementation.

---

## Decisions Affecting Roadmap

| ADR | Decision | Impact |
|-----|----------|--------|
| ADR-003 | One resource file per topic, web-fetched | All phases |
| ADR-002 | [check 00-system/decisions/] | TBD |
| ADR-001 | [check 00-system/decisions/] | TBD |

---

## Learning Style Rules (Permanent)

- Caveman/ultra mode = default
- .NET analogies OK
- Practical > theory always
- Consultant framing at every topic
- Client-ready language in use cases
- Generate resource file immediately after each topic (not deferred)
