# NEXT-SESSION.md — AgenticAI Learning OS
<!-- ONE FILE = FULL CONTEXT. Load this at start of every Claude.AI session. -->
<!-- Raw URL: https://raw.githubusercontent.com/pankildesai1988/AgenticAI/main/NEXT-SESSION.md -->
<!-- ⚠️ Always committed before session ends. Never trust platform memory. GitHub = SSOT. -->

---

## SESSION RESUME POINT
STATE_VERSION=v7
GENERATED=2026-05-27
GENERATED_BY=Claude (claude.ai chat, caveman/ultra mode)
CURRENT_PHASE=P01
CURRENT_TOPIC=T2 — Prompt Patterns
PHASE_STATUS=IN_PROGRESS
CUT_POINT=NONE — T1 complete. Begin P01-T2 fresh.
NEXT_STEP=Start P01-T2 Prompt Patterns. Cover zero-shot, few-shot, chain-of-thought. Use UpworkAgent + ArNir examples.
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
- Attention mechanism + how RAG + Attention combine ✅ (P00-T3)
- API parameters + cost math + Router Agent pattern ✅ (P00-T4)
- Agent vs chatbot + ReAct + Planner+Tools+Memory model ✅ (P00-T5)
- Prompt anatomy: instruction strength, role/context, task/format, constraints ✅ (P01-T1)
- Prompt patterns: NOT STARTED → P01-T2

Do NOT re-explain: RAG basics ✅, token explanation ✅, chatbot vs agent ✅, prompt anatomy 4 parts ✅

---

## ACTIVE PROJECTS
- ArNir: enterprise AI platform (.NET Core net9, pgvector, RAG, OpenAI/Claude/Gemini)
  Status: chatbot today. Missing: tool registry + ReAct loop wiring (Semantic Kernel)
  Next upgrade: wire existing RAG as Tool 1 in Semantic Kernel agent pipeline
  P01-T1 output: RAG response format spec done (JSON: answer + confidence + source_chunks_used)
- UpworkAgent OS: hybrid .NET/Python agentic freelance automation
  Status: full prompt architecture designed this session
  DB schema: PromptTemplates + ProposalLog tables designed
  Job analysis prompt: JSON output with fit_score, bid_recommendation, suggested_hook
  Proposal prompt: HOOK/CREDIBILITY/APPROACH/DIFFERENTIATOR/CTA structure
  AI improvement loop: response rate tracking → auto prompt versioning designed
- This Learning OS: P00 complete, P01 T1 complete (20% P01)

---

## CURRENT PHASE CONTEXT
Phase: P01 — Prompt Engineering
Topics:
  T1: Prompt anatomy ✅ DONE
  T2: Prompt patterns (zero-shot, few-shot, chain-of-thought) ← NEXT
  T3: System prompts + temperature + model selection (tone topic parked here from T1)
  T4: Prompt engineering for ArNir (production prompts)
  T5: Prompt evaluation + iteration + consultant delivery

Parked for T3: Tone types (consultant/collaborative/formal/empathetic) + when to use each

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