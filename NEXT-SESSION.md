# NEXT-SESSION.md — AgenticAI Learning OS
<!-- ONE FILE = FULL CONTEXT. Load this at start of every Claude.AI session. -->
<!-- Raw URL: https://raw.githubusercontent.com/pankildesai1988/AgenticAI/main/NEXT-SESSION.md -->
<!-- ⚠️ Always committed before session ends. Never trust platform memory. GitHub = SSOT. -->

---

## SESSION RESUME POINT
STATE_VERSION=v9
GENERATED=2026-05-29
GENERATED_BY=Claude (claude.ai chat, caveman/ultra mode)
CURRENT_PHASE=P01
CURRENT_TOPIC=T5 — Prompt Evaluation + Iteration + Consultant Delivery
PHASE_STATUS=IN_PROGRESS
CUT_POINT=NONE — T4 complete + ArNir Doc Q&A shipped. Begin T5 fresh.
NEXT_STEP=Start P01-T5. Ask: "ArNir system prompt is live. How do you know if it's getting better or worse? What would you measure?" Then build eval loop.
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
- ArNir production prompts + PDF viewer + highlight + trust gap demo ✅ (P01-T4)
- Prompt evaluation + iteration: NOT STARTED → P01-T5

Do NOT re-explain: RAG ✅, tokens ✅, chatbot vs agent ✅, prompt anatomy ✅, zero/few/CoT ✅, temperature ✅, system prompt 5-part ✅

---

## ACTIVE PROJECTS
- ArNir: enterprise AI platform (.NET Core net9, pgvector, RAG, OpenAI/Claude/Gemini)
  SHIPPED T4: PDF inline viewer + source highlight. Healthcare demo complete. 76+37+13 tests green.
  System prompt: 5-part, RAG-only, JSON with bbox + confidence ✅
  Next: extend to ecommerce + finance demos OR productionize PDF storage (S3/Blob)
  Project note: `07-projects/arnir/arnir-document-qa-feature.md`
- UpworkAgent OS: hybrid .NET/Python agentic freelance automation
  Proposal prompt v2: 7 fixes applied ✅
  Job scoring: CoT + few-shot + reasoning_steps ✅
  PENDING: paste 1 real winning proposal as few-shot example
  PENDING: apply 7 Python fixes to _draft_with_claude
- This Learning OS: P00 complete ✅, P01 T1-T4 complete (80% P01)

---

## CURRENT PHASE CONTEXT
Phase: P01 — Prompt Engineering
Topics:
  T1: Prompt anatomy ✅ DONE
  T2: Prompt patterns (zero-shot, few-shot, CoT) ✅ DONE
  T3: System prompts + temperature + model selection ✅ DONE
  T4: ArNir production prompts + Doc Q&A feature ✅ DONE + SHIPPED
  T5: Prompt evaluation + iteration + consultant delivery ← NEXT

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