# NEXT-SESSION.md — AgenticAI Learning OS
<!-- ONE FILE = FULL CONTEXT. Load this at start of every Claude.AI session. -->
<!-- Raw URL: https://raw.githubusercontent.com/pankildesai1988/AgenticAI/main/NEXT-SESSION.md -->
<!-- ⚠️ Always committed before session ends. Never trust platform memory. GitHub = SSOT. -->

---

## SESSION RESUME POINT
STATE_VERSION=v6
GENERATED=2026-05-25
GENERATED_BY=Claude (claude.ai chat + Claude Code)
CURRENT_PHASE=P01
CURRENT_TOPIC=T1 — Prompt Anatomy
PHASE_STATUS=NOT_STARTED
CUT_POINT=NONE — Clean start. P00 complete. Begin P01-T1 fresh.
NEXT_STEP=Start P01 Prompt Engineering. Entry: Pankil uses prompts daily but doesn't know WHY they work or fail. Begin with prompt anatomy (role/task/context/format).
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

## WHAT PANKIL KNOWS (cumulative — P00 complete)
- AI/ML/DL/GenAI hierarchy map ✅ (P00-T1)
- Tokens/embeddings/context window/RAG + cost math ✅ (P00-T2)
- Attention mechanism + how RAG + Attention combine ✅ (P00-T3)
- API parameters + cost math + Router Agent pattern ✅ (P00-T4)
- Agent vs chatbot + ReAct + Planner+Tools+Memory model ✅ (P00-T5)
- Prompt engineering: NOT STARTED → P01

Do NOT re-explain: RAG basics ✅, token explanation ✅, chatbot vs agent ✅, REST stateless analogy ✅

---

## ACTIVE PROJECTS
- ArNir: enterprise AI platform (.NET Core net9, pgvector, RAG, OpenAI/Claude/Gemini)
  Status: chatbot today. Missing: tool registry + ReAct loop wiring (Semantic Kernel)
  Next upgrade: wire existing RAG as Tool 1 in Semantic Kernel agent pipeline
- UpworkAgent OS: hybrid .NET/Python agentic freelance automation
  Status: Router Agent pattern from P00-T4 ready to integrate
- This Learning OS: P00 complete (10%), P01 starting next session

---

## CURRENT PHASE CONTEXT
Phase: P01 — Prompt Engineering
Entry gap: Pankil uses prompts daily (Claude/ChatGPT/Gemini/Perplexity) but doesn't know WHY they work or fail
Goal: systematic prompt engineering for consulting use + ArNir production prompts
Topics (to be confirmed at P01 start):
  T1: Prompt anatomy (role/task/context/format)
  T2: Prompt patterns (zero-shot, few-shot, chain-of-thought)
  T3: System prompts + temperature + model selection
  T4: Prompt engineering for ArNir (production prompts)
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
Example: `P01-T2: Covered zero-shot + few-shot patterns. NOT YET covered chain-of-thought. Next: CoT with ArNir menu-recommendation example.`
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
   Goal: NEXT-SESSION.md stays ≤ 150L forever (P09 complete ≈ 125L).
