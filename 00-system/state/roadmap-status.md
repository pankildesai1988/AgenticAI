# Roadmap Status
<!-- Max 150 lines. Update each phase completion. -->

## Phase Overview

| Phase | Name | Status | Progress | Completed |
|-------|------|--------|----------|-----------|
| P00 | AI Foundation | ✅ COMPLETE | 100% | 2026-05-25 |
| P01 | Prompt Engineering | 🔄 IN PROGRESS | 80% | - |
| P02 | RAG Deep Dive | ⏳ Pending | 0% | - |
| P03 | Agentic Patterns | ⏳ Pending | 0% | - |
| P04 | Multi-Agent Systems | ⏳ Pending | 0% | - |
| P05 | Tool Use & MCP | ⏳ Pending | 0% | - |
| P06 | Memory Systems | ⏳ Pending | 0% | - |
| P07 | Production AI | ⏳ Pending | 0% | - |
| P08 | Consulting Playbook | ⏳ Pending | 0% | - |
| P09 | Capstone Projects | ⏳ Pending | 0% | - |

**Overall: 18% (P00 complete + P01 80%)**

---

## P00 — AI Foundation ✅ COMPLETE
- P00: AI Foundation ✅ (foundation map, tokens/RAG, attention, API cost, agent mental models)

---

## P01 — Prompt Engineering 🔄 IN PROGRESS (80%)

**Topics:**
- T1: Prompt anatomy (4-part, instruction strength, formats, constraints) ✅
- T2: Patterns (zero-shot, few-shot, CoT, combined) ✅
- T3: System prompts (5-part), 9 tones, temperature, model selection ✅
- T4: ArNir production prompts + Doc Q&A feature SHIPPED ✅
- T5: Prompt evaluation + iteration + consultant delivery ← NEXT

**Key outputs this phase:**
- UpworkAgent proposal prompt v2 (7 fixes from v1)
- UpworkAgent job scoring: CoT + few-shot + reasoning_steps
- ArNir system prompt: 5-part, RAG-only, JSON + bbox + confidence
- ArNir healthcare demo: PDF viewer + highlight (trust gap closed)
- 07-projects/ folder + first project note

---

## P02 — RAG Deep Dive ⏳

**Topics planned:**
- Vector DB architecture (pgvector deep dive)
- Chunking strategies
- Embedding model selection
- Hybrid search (semantic + keyword)
- Reranking + evaluation

**Pankil's edge:** pgvector already in ArNir + bbox chunking now in place. Will optimize existing.

---

## Repo Structure Status

| Folder | Status | Notes |
|--------|--------|-------|
| 00-system/ | ✅ Active | ADRs 0001-0007 |
| 01-memory/ | ✅ Active | Session snapshots |
| 02-learning/ | ✅ Active | P00 complete, P01 in progress |
| 03-prompts/ | ✅ Active | master-session-end-prompt, proposal prompt v2 |
| 04-business/ | ⏳ Not created | Planned |
| 05-debugging/ | ⏳ Not created | Planned |
| 06-prompts/ | ⏳ Not created | Planned |
| 07-projects/ | ✅ CREATED | arnir-document-qa-feature.md |
| 08-meta/ | ⏳ Not created | Planned |
| AI-HANDOFF/ | ✅ Active | Claude, ChatGPT, Gemini, Perplexity |

---

## Learning Style Rules (Permanent)
- Caveman/ultra mode = default
- .NET analogies OK
- Practical > theory always
- Consultant framing at every topic
- Client-ready language in use cases
- Generate resource file immediately after each topic (not deferred)