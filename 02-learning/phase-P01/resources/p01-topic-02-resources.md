# P01 · Topic 2: Prompt Patterns
**Phase:** P01 Prompt Engineering
**Status:** Reference material — use AFTER completing Topic 2 learning
**Last Updated:** 2026-05-29
**Rule:** Generated after topic completed. Web-fetched for freshness.

---

## 🗺️ The Map (Quick Recap)

```
Zero-shot  → instructions only. No examples. AI guesses format + quality.
Few-shot   → instructions + examples. AI anchors to your examples.
CoT        → force AI to reason step by step BEFORE answering.

.NET analogy:
Zero-shot  = method call with no unit tests. Hope it works.
Few-shot   = method call with XML doc examples showing input/output.
CoT        = method with step-by-step inline comments + logs before return.
```

**When to use which:**
```
Zero-shot  → simple, well-defined, format never drifts
Few-shot   → output format critical, edge cases exist
CoT        → ambiguous input, multi-factor decision, need audit trail
Combined   → CoT + few-shot = highest reliability for complex tasks

UpworkAgent job scoring  → CoT + Few-shot (multi-factor + audit trail)
ArNir RAG response       → Few-shot (JSON format must be exact)
Simple classification    → Zero-shot (fast, cheap)
```

**CoT in practice:**
```
THINK STEP BY STEP before scoring:
1. Skill match — required skills present?
2. Location — US/Canada restriction? → penalty
3. Budget — reasonable for scope?
4. Role type — dev work or comms-only?
5. Negative keywords — present? → score 0
THEN return JSON.
```

---

## 📰 Blog / Article

| # | Title | Link | Summary |
|---|-------|------|---------|
| 1 | **Chain-of-Thought Prompting Guide** | [prompthub.us](https://www.prompthub.us/blog/chain-of-thought-prompting-guide) | • Few-shot CoT beats zero-shot CoT on complex reasoning tasks • Self-consistency extension: run CoT multiple times, pick most consistent answer → reduces one-off errors • Step-Back prompting: ask AI to reason about high-level concepts first before solving • Best for: production reliability when output must be correct, not just plausible |
| 2 | **Chain-of-Thought Prompting — Analytics Vidhya** | [analyticsvidhya.com](https://www.analyticsvidhya.com/blog/2025/12/chain-of-thought-cot-prompting/) | • Few-shot prompting improves accuracy vs zero-shot, but struggles with multi-step reasoning alone • CoT fixes multi-step gap by injecting reasoning steps as intermediate output • Key finding: LLMs generalize well even when example labels are randomized — format matters more than perfect examples • Best for: understanding WHY CoT works, not just how |
| 3 | **Zero-Shot CoT Guide 2025** | [shadecoder.com](https://www.shadecoder.com/topics/zero-shot-cot-a-comprehensive-guide-for-2025) | • "Think step by step" = zero-shot CoT trigger. Works surprisingly well on modern models. • Two-pass flow: generate CoT reasoning → verify final answer → mitigates incorrect leaps • Common mistake: ambiguous prompt → AI unsure how to structure reasoning → use concise explicit instructions • Best for: quick CoT without writing examples (prototype fast) |
| 4 | **Prompt Engineering Guide — promptingguide.ai** | [promptingguide.ai](https://www.promptingguide.ai/techniques/cot) | • Auto-CoT: clusters examples by similarity, auto-samples diverse examples → removes manual example writing burden • CoT performance gains kick in at large model scale (~100B+ params) → Claude/GPT-4 class models = CoT works well • Best reference for: all CoT variants (standard, zero-shot, auto, self-consistency) in one place |

---

## 🎥 YouTube Video (Long Form)

| # | Title | Link | Summary |
|---|-------|------|---------|
| 1 | **Prompt Engineering Full Course — LearnPrompting** | [learnprompting.org](https://learnprompting.org) | • Covers zero-shot → few-shot → CoT progression with code examples • Shows real before/after output comparisons for each pattern • Includes Tree of Thoughts + ReAct as advanced extensions • Best for: 2-hour deep dive covering all patterns in one session |

---

## 📱 YouTube Short / Quick Reference

| # | Title | Link | Summary |
|---|-------|------|---------|
| 1 | **Prompt Report 2025 — 6 Core Techniques** | [arxiv.org](https://arxiv.org/pdf/2509.11295) | • 58 prompting techniques distilled to 6 that matter: zero-shot, few-shot, thought generation, ensembling, self-criticism, decomposition • Self-criticism = ask AI to review its own answer before finalizing → free quality check • Decomposition = break complex task into sub-tasks → each easier to solve • Best for: 15-min read showing where CoT fits in the full prompt engineering landscape |

---

## 🏢 Real Business Use Cases

| Scenario | Pattern | Why |
|----------|---------|-----|
| UpworkAgent job scoring | CoT + Few-shot | Multi-factor decision + audit trail for improvement loop |
| ArNir RAG response | Few-shot | JSON format (answer/confidence/source) must be exact |
| Proposal hook generation | Few-shot | Examples teach AI your voice and style |
| Legal clause analysis | CoT | Multi-step: find clause → compare → flag → draft |
| Restaurant menu recommendation | CoT | Multi-factor: dietary, budget, occasion, table size |
| Simple intent classification | Zero-shot | Binary result, no format complexity |
| Bug triage system | CoT + Few-shot | Severity scoring needs step-by-step + anchored examples |

---

## 💡 UpworkAgent OS — What You Built This Session

```
Job Scoring Prompt (CoT + Few-shot combined):

STEP 1: Skill match — C#/ASP.NET Core/SQL present?
STEP 2: Location check — US/Canada only? → -30 penalty
STEP 3: Budget — stated? reasonable?
STEP 4: Role type — dev or comms-only?
STEP 5: Negative keywords → score 0

EXAMPLE 1 (few-shot anchor — score 18):
  Client comms role, native English required, US/Canada preferred
  → {"fit_score": 18, "bid_recommendation": "skip", "reason": "..."}

EXAMPLE 2 (few-shot anchor — score 86):
  Pure .NET bug fix, EF Core, Razor Pages
  → {"fit_score": 86, "bid_recommendation": "bid", "reason": "..."}

Output includes reasoning_steps → feeds improvement loop in ProposalLog DB
```

**Why reasoning_steps matters:**
```
Store in DB → find patterns where AI scored wrong → fix prompt → version up
Explainable AI → client asks "why skip?" → show reasoning_steps
```

---

## 🔑 Key Insight This Session

> Few-shot teaches AI what YOUR good looks like.
> CoT forces AI to show its work before answering.
> Combined = consistent output + audit trail + improvement loop fuel.

---

## ✅ After Reading Checklist

- [ ] Can define zero-shot, few-shot, CoT in one sentence each
- [ ] Know when to use each pattern (task complexity guide)
- [ ] Understand few-shot examples = output format + quality anchor
- [ ] Know CoT = step-by-step reasoning BEFORE final answer
- [ ] Can explain reasoning_steps field value to a client (explainable AI)
- [ ] Know CoT + few-shot combined = highest reliability pattern
- [ ] Applied both patterns to UpworkAgent job scoring prompt

---

## 🔗 Related

- Previous: `p01-topic-01-resources.md`
- Next: `p01-topic-03-resources.md`
- ADR: `00-system/decisions/ADR-0005-resource-format.md`
