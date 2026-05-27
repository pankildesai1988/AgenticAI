# P01 · Topic 1: Prompt Anatomy
**Phase:** P01 Prompt Engineering  
**Status:** Reference material — use AFTER completing Topic 1 learning  
**Last Updated:** 2026-05-27  
**Rule:** Generated after topic completed. Web-fetched for freshness.

---

## 🗺️ The Map (Quick Recap)

```
PROMPT ANATOMY = 4 PARTS
─────────────────────────────────────────────────────────
PART 1: INSTRUCTION STRENGTH
  Weak  → too / also / add / make sure / don't forget
  Strong → MUST / ALWAYS / REQUIRED / CONSTRAINT / DO NOT

PART 2: ROLE + CONTEXT
  Role    = WHO AI is        → interface contract (C# analogy)
  Context = WHAT EXISTS      → constructor inject (C# analogy)
  No Role    → AI picks random behavior
  No Context → AI works with null data → NullReference response

PART 3: TASK + FORMAT
  Task   = WHAT to do        → be specific, numbered if multi-step
  Format = HOW to return it  → JSON / Markdown / Table / Steps
  No Format → same prompt, different day, different structure
  With Format → parseable, automatable, consistent

PART 4: CONSTRAINTS
  Negative    → DO NOT use: "guaranteed", "expert", "highly skilled"
  Boundary    → if fit_score < 6 → bid_recommendation = false always
  Behavioral  → if answer not in context → say "Not found in documents"
─────────────────────────────────────────────────────────
```

**Key insight from session:**
> Prompt = HTTP request. Vague URL → wrong route. Structured payload → correct response.
> Role = interface contract. Context = constructor inject. Format = response DTO. Constraints = guard clauses.

**Real bug diagnosed this session:**
```
BROKEN prompt: "Add the Masquerade user detail in printable area too."
ROOT CAUSE:
  - "too" = weak instruction → AI treated as optional
  - Requirement buried in last sentence → AI deprioritized it
  - No constraint enforcing it → AI skipped it

FIX:
  - "Masqueraded user name + role MUST appear in print header"
  - Move to dedicated CONSTRAINTS section
  - "REQUIRED on every print page — not optional"
```

---

## 📰 Blog / Article

| # | Title | Link | Summary |
|---|-------|------|---------|
| 1 | **Anatomy of a Prompt for AI Assistants** | [kirschbaumdevelopment.com](https://kirschbaumdevelopment.com/insights/anatomy-of-a-prompt-for-ai-assistants) | • Breaks down Role/Context/Task/Format/Constraints with developer examples • Key: each section reduces uncertainty and focuses model effort • "Guides AI with context, gives data to act on, states task, describes output format, sets constraints" • Best for: bookmark as daily reference when writing prompts |
| 2 | **The 3-Layer Prompt Template for Consistent Results** | [dev.to](https://dev.to/novaelvaris/the-3-layer-prompt-template-for-consistent-results-context-task-constraints-ic4) | • CONTEXT/TASK/CONSTRAINTS framework — maps directly to T1 anatomy • Key rule: "Good context = role + artifacts + goal of larger system" • Anti-goal pattern: MUST AVOID section prevents AI drift • Best for: copy-paste template when building UpworkAgent + ArNir prompts |
| 3 | **A Practitioner's Guide to Prompt Engineering 2025** | [getmaxim.ai](https://www.getmaxim.ai/articles/a-practitioners-guide-to-prompt-engineering-in-2025/) | • Production-grade: treats prompt engineering as a lifecycle (design → evaluate → iterate) • Controllability = consistent formats, schema adherence, deterministic behavior under constraints • Connects to UpworkAgent: prompt versioning = lifecycle management • Best for: senior devs building production LLM apps like ArNir |
| 4 | **Prompt Structure: Role → Task → Style → Format → Constraints** | [impranjalk.com](https://impranjalk.com/prompt-structure-breakdown/) | • 5-part formula with real examples for each part • Without role = generic response. With role = domain-specific, tailored output • Covers Style (tone) separately — maps to P01-T3 parked topic • Best for: client-facing explanation of WHY structured prompts matter |

---

## 🎥 YouTube Video (Long Form)

| # | Title | Link | Summary |
|---|-------|------|---------|
| 1 | **Prompt Engineering 2025: What Works and What Doesn't** | [youtube.com — Sander Schulhoff](https://lilys.ai/en/notes/prompt-engineering-20251025/) | • Covers role framing, constraint design, format specification with real examples • Key stat: businesses with proper prompt engineering see 60-70% efficiency gains • Explains why "how you ask" matters as much as "what you ask" • Best for: 1-hour watch before building ArNir production system prompts |

---

## 📱 YouTube Short / Quick Read

| # | Title | Link | Summary |
|---|-------|------|---------|
| 1 | **2025 Beginner's Guide to Prompt Engineering** | [medium.com](https://medium.com/@hamzamaq96/2025-beginners-guide-to-prompt-engineering-step-by-step-roadmap-2b3435eac54a) | • "Every prompt: Role + Task + Tone" → 3-part minimum viable prompt • Key insight: using "list" vs "explain" vs "guide" gives AI different context • Word choice = seasoning in a recipe → nudges AI in nuanced ways • Best for: 10-min read to reinforce T1 anatomy before T2 patterns |

---

## 📘 Deep Dive

| # | Title | Link | Summary |
|---|-------|------|---------|
| 1 | **What I Learned About Prompt Engineering in 2025** | [medium.com](https://medium.com/@lorenzouriel/what-i-learned-about-prompt-engineering-in-2025-c232ff27d678) | • Context > Role > Expectation (CRE) framework — alternative framing of T1 • Key: "explicitly instruct model to reason step-by-step" = CoT preview (T2) • Format spec: specify sections, bullet points, tables, schemas, code blocks • Best for: reading between T1 and T2 — bridges anatomy to patterns |

---

## 💡 Instruction Strength Cheat Sheet

| Weak Word | Strong Word | Use When |
|-----------|-------------|----------|
| too / also | MUST | Critical non-optional requirement |
| add | REQUIRED: | Feature that cannot be skipped |
| keep it | DO NOT change | Design/content that must stay fixed |
| make sure | ALWAYS | Behavior that must be consistent |
| don't forget | CONSTRAINT: | Hard rule with zero exceptions |
| try to | NEVER | Absolute prohibition |

---

## 🏢 Real Business Use Cases

| Scenario | Anatomy Fix | Result |
|----------|-------------|--------|
| Masquerade print bug | Moved req to CONSTRAINT section + changed "too" → "MUST" | AI cannot skip it |
| ArNir RAG answer | Format: JSON (answer + confidence + source_chunks_used) | UI can show confidence badge |
| UpworkAgent job analysis | Format: JSON with fit_score, bid_recommendation | C# can process programmatically |
| UpworkAgent proposal | Constraints: no "guaranteed/expert", start with client pain, 150-200 words | Ready-to-send output |
| Client audit (consulting) | Use T1 checklist: Role? Context? Format? Constraints? | Billable prompt audit service |

---

## 💡 ArNir Production Prompt — T1 Applied

```
Role: You are ArNir, enterprise document assistant.
      Answer ONLY from provided document context.
      If answer not found → return "Not available in documents."

Context: User query matched against pgvector embeddings.
         Top-K relevant chunks injected: {rag_chunks}
         Answer strictly from these chunks only.

Task: Answer user query based on context chunks provided.

Format: Return JSON only. No markdown wrapper. No explanation.
{
  "answer": "<response to user query>",
  "confidence": "High" | "Medium" | "Low",
  "source_chunks_used": <1-5>
}

Constraints:
- DO NOT hallucinate dates, numbers, or names
- DO NOT combine info from unrelated chunks
- If confidence Low → append: "Please verify with source document"
- Max answer: 150 words
- Language: match user query language
```

---

## 💡 UpworkAgent OS Prompt — T1 Applied

```
Role: You are an expert Upwork proposal writer for Pankil Desai,
      senior Agentic AI Consultant (15yr .NET background).
      Write consultant-tone proposals. Position as problem-solver, not coder.

Context:
- Pankil expertise: {expertise_tags}
- Relevant portfolio: {portfolio_items} (AI-selected per job)
- Job details: {job_title}, {job_description}, {client_budget}

Task: Write structured proposal draft.

Format:
  HOOK (1 sentence): Mirror client's problem using their exact words.
  CREDIBILITY (2 sentences): Relevant experience + proof.
  APPROACH (3-4 sentences): How you solve THIS specific problem.
  DIFFERENTIATOR (1 sentence): Why Pankil vs 50 other bidders.
  CTA (1 sentence): Low-friction next step.

Constraints:
- DO NOT use: "guaranteed", "best", "expert", "highly skilled"
- DO NOT start with "I"
- Start with client pain (mirror their words)
- Length: 150-200 words HARD limit
- If fit_score < 6 → do not generate proposal
```

---

## ✅ After Reading Checklist

- [ ] Know 4 parts of prompt anatomy: Instruction Strength / Role+Context / Task+Format / Constraints
- [ ] Can audit a broken prompt and identify which part is missing
- [ ] Know instruction strength cheat sheet (MUST vs too)
- [ ] Understand Role = interface contract, Context = constructor inject (.NET analogy)
- [ ] Know 4 format types: JSON / Markdown / Table / Steps — and when to use each
- [ ] Know 3 constraint types: Negative / Boundary / Behavioral
- [ ] Can write ArNir system prompt with JSON format + confidence spec
- [ ] Can write UpworkAgent proposal prompt with HOOK/CREDIBILITY/APPROACH/DIFF/CTA
- [ ] Can position prompt audit as consulting deliverable (billable skill)

---

## 🎓 Consultant Pitch Developed This Session

**Prompt Audit Service:**
> "I can audit your existing AI prompts and identify exactly why they produce inconsistent output.
> Most broken prompts fail on one of four things: no role defined, missing context,
> no format spec, or weak constraint language.
> One session → structured prompt → 60-70% better output consistency."

**Mirror Hook technique (Upwork):**
> "Your support team is drowning in repetitive tickets that your knowledge base
> already has answers to — you just need the right AI agent to connect them."

---

## 🔗 Related

- Previous Phase: `02-learning/phase-P00/resources/p00-topic-05-resources.md`
- Next: `p01-topic-02-resources.md` (Prompt Patterns — zero-shot, few-shot, CoT)
- Master prompt: `03-prompts/master-session-end-prompt.md`
- ADR: `00-system/decisions/ADR-0005-resource-format.md`
