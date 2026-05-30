# Roadmap Status
<!-- Max 150 lines. Update each phase completion. -->

## Phase Overview

| Phase | Name | Status | Progress | Completed |
|-------|------|--------|----------|-----------|
| P00 | AI Foundation | ✅ COMPLETE | 100% | 2026-05-25 |
| P01 | Prompt Engineering | ✅ COMPLETE | 100% | 2026-05-30 |
| P02 | RAG Deep Dive | ⏳ Pending | 0% | - |
| P03 | Agentic Patterns | ⏳ Pending | 0% | - |
| P04 | Multi-Agent Systems | ⏳ Pending | 0% | - |
| P05 | Tool Use & MCP | ⏳ Pending | 0% | - |
| P06 | Memory Systems | ⏳ Pending | 0% | - |
| P07 | Production AI | ⏳ Pending | 0% | - |
| P08 | Consulting Playbook | ⏳ Pending | 0% | - |
| P09 | Capstone Projects | ⏳ Pending | 0% | - |

**Overall: 20% (P00 + P01 complete)**

---

## P00 — AI Foundation ✅ COMPLETE (2026-05-25)
- P00: AI Foundation ✅ (foundation map, tokens/RAG, attention, API cost, agent mental models)
- Mind maps: p00-topic-01 through p00-topic-05 + p00-phase-mindmap ✅

---

## P01 — Prompt Engineering ✅ COMPLETE (2026-05-30)
- P01: Prompt Engineering ✅ (anatomy, zero/few/CoT, system prompts, ArNir production, eval loop)
- Mind maps: p01-topic-01 through p01-topic-05 + p01-phase-mindmap ✅

**Key outputs:**
- UpworkAgent proposal prompt v2 (7 fixes from v1)
- UpworkAgent job scoring: CoT + few-shot + reasoning_steps
- ArNir system prompt: 5-part, RAG-only, JSON + bbox + confidence
- ArNir healthcare demo: PDF viewer + highlight shipped ✅
- Evaluation dashboard: LLM-as-Judge R+F scores live ✅
- HITL design: ticket + live chat for 0.00 score routing
- Feedback loop: ticket answer → pgvector pattern
- ADR-0008: Visual mind map PNG protocol
- 12 mind map PNGs generated (P00 + P01 all topics + phases)

---

## P02 — RAG Deep Dive ⏳ NEXT

**Topics planned:**
- T1: Vector DB architecture (pgvector deep dive)
- T2: Chunking strategies (text, table, image, bbox)
- T3: Embedding model selection + comparison
- T4: Hybrid search (semantic + keyword BM25)
- T5: Reranking + RAG evaluation metrics

**Pankil's edge:** pgvector + bbox chunking already in ArNir. Will optimize + extend existing.

---

## Repo Structure Status

| Folder | Status | Notes |
|--------|--------|-------|
| 00-system/ | ✅ Active | ADRs 0001-0008 |
| 01-memory/ | ✅ Active | Session snapshots |
| 02-learning/ | ✅ Active | P00+P01 complete, mindmaps/ folders added |
| 03-prompts/ | ✅ Active | master-session-end-prompt v2.0, proposal prompt v2 |
| 07-projects/ | ✅ Active | arnir-document-qa-feature.md |
| AI-HANDOFF/ | ✅ Active | Claude, ChatGPT, Gemini, Perplexity |

---

## Learning Style Rules (Permanent)
- Caveman/ultra mode = default
- .NET analogies OK
- Practical > theory always
- Consultant framing at every topic
- Client-ready language in use cases
- Generate resource file + PNG immediately after each topic (not deferred)
