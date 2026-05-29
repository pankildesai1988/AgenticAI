# NEXT-SESSION.md — AgenticAI Learning OS
<!-- ONE FILE = FULL CONTEXT. Load this at start of every Claude.AI session. -->
<!-- Raw URL: https://raw.githubusercontent.com/pankildesai1988/AgenticAI/main/NEXT-SESSION.md -->
<!-- ⚠️ Always committed before session ends. Never trust platform memory. GitHub = SSOT. -->

---

## SESSION RESUME POINT
STATE_VERSION=v8
GENERATED=2026-05-29
GENERATED_BY=Claude (claude.ai chat, caveman/ultra mode)
CURRENT_PHASE=P01
CURRENT_TOPIC=T4 — Prompt Engineering for ArNir (Production Prompts)
PHASE_STATUS=IN_PROGRESS
CUT_POINT=NONE — T2 + T3 complete. Begin P01-T4 fresh.
NEXT_STEP=Start P01-T4. Ask Pankil: "What are the 3 most common query types your ArNir clients ask?" Then build production prompts for each.
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

---

## WHAT PANKIL KNOWS (cumulative)
- AI/ML/DL/GenAI hierarchy map ✅ (P00-T1)
- Tokens/embeddings/context window/RAG + cost math ✅ (P00-T2)
- Attention mechanism + RAG + Attention combine ✅ (P00-T3)
- API parameters + cost math + Router Agent pattern ✅ (P00-T4)
- Agent vs chatbot + ReAct + Planner+Tools+Memory model ✅ (P00-T5)
- Prompt anatomy: instruction strength, role/context, task/format, constraints ✅ (P01-T1)
- Prompt patterns: zero-shot, few-shot, CoT, combined ✅ (P01-T2)
- System prompts (5-part), 9 tone types, temperature, model selection ✅ (P01-T3)
- ArNir production prompts: NOT STARTED → P01-T4

Do NOT re-explain: RAG ✅, tokens ✅, chatbot vs agent ✅, prompt anatomy ✅, zero/few/CoT ✅, temperature ✅

---

## ACTIVE PROJECTS
- ArNir: enterprise AI platform (.NET Core net9, pgvector, RAG, OpenAI/Claude/Gemini)
  Status: chatbot today. Missing: tool registry + ReAct loop (Semantic Kernel)
  System prompt rebuilt this session: 5-part structure, RAG-only, JSON format spec
  Next: build production prompts for top 3 ArNir query types (T4)
- UpworkAgent OS: hybrid .NET/Python agentic freelance automation
  Proposal prompt v2 generated: 7 fixes applied vs v1
  Job scoring: CoT + few-shot combined, reasoning_steps in JSON
  Python _draft_with_claude: 7 issues identified (RateLimitError bug, regex JSON, logging, temp)
  PENDING: paste 1 real winning proposal as few-shot example before production deploy
  PENDING: apply 7 Python code fixes
- This Learning OS: P00 complete, P01 T1+T2+T3 complete (60% P01)

---

## CURRENT PHASE CONTEXT
Phase: P01 — Prompt Engineering
Topics:
  T1: Prompt anatomy ✅ DONE
  T2: Prompt patterns (zero-shot, few-shot, CoT) ✅ DONE
  T3: System prompts + temperature + model selection + 9 tone types ✅ DONE
  T4: Prompt engineering for ArNir (production prompts) ← NEXT
  T5: Prompt evaluation + iteration + consultant delivery

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
3. List all resource files generated this session (pending git commit)
4. Commit message format: `feat(P[XX]): [what was done]`
5. DO NOT end session without completing this block
6. Phase complete → collapse WHAT PANKIL KNOWS:
   Replace 5 topic lines with 1 summary: `P[XX]: [Phase Name] ✅ ([keyword, keyword, keyword])`
   Keep current phase topics expanded until that phase completes.
   Goal: NEXT-SESSION.md stays ≤ 150L forever.
