# P00 · Topic 5: Mental Models for Agentic AI
**Phase:** P00 AI Foundation  
**Status:** Reference material — use AFTER completing Topic 5 learning  
**Last Updated:** 2026-05-25  
**Rule:** Generated after topic completed. Web-fetched for freshness.

---

## 🗺️ The Map (Quick Recap)

```
CHATBOT                          AGENT
────────────────────────────────────────────────
Input:   User query               User GOAL
Process: Single LLM call          Plan → multi-step
Tools:   ❌ None                  ✅ PDF, CRM, DB, API
Memory:  Session only             Persistent (pgvector)
Output:  Text response            Goal achieved
Flow:    YOUR code decides        LLM decides at runtime
```

**Agent = Planner + Tools + Memory + ReAct Loop**

```
ReAct Loop (what LLM does internally):
Reason  → "Invoice found. No discrepancy. Skip flag step."
Act     → Call next tool OR stop
Observe → Read tool result
Reason  → "Is goal achieved? Yes/No?"
Repeat until done.
```

**Your Restaurant Agent Proposal (real consulting output):**
```
User goal → Intent analysis
         → Plan steps
         → Execute tools
         → Store in DB (memory)

Value delivered:
  Customer  → finds right menu item
  Staff     → knows what customer needs
  Owner     → trending items dashboard + inventory planning
```

---

## 📰 Blog / Article

| # | Title | Link | Summary |
|---|-------|------|---------|
| 1 | **The Agentic AI Handbook — FreeCodeCamp** | [freecodecamp.org](https://www.freecodecamp.org/news/the-agentic-ai-handbook/) | • ReAct loop explained: Thought (LLM reasoning) → Action (tool call) → Observation → repeat • Plan-and-Execute: LLM plans full strategy first, then executor runs each step • Multi-agent: multiple LLMs with different roles (planner, analyst, critic) • Best for: complete beginner-to-intermediate agentic AI overview |
| 2 | **Agentic Reasoning Patterns: 4 Frameworks** | [servicesground.com](https://servicesground.com/blog/agentic-reasoning-patterns/) | • Covers ReAct, Reflexion, Plan-and-Execute, Tree of Thoughts • Reflexion = agent that self-critiques and learns from mistakes • PRAR loop: Perception → Reasoning → Action → Reflection • Best for: understanding WHICH pattern to use for which problem |
| 3 | **AI Agent vs Chatbot: What's the Real Difference** | [wotnot.io](https://wotnot.io/blog/ai-agent-vs-chatbot) | • Chatbot = script follower. Agent = goal achiever • 2025: chatbots no longer the endgame — agents replacing them • Real examples: customer service chatbot vs support agent • Best for: client-facing language to explain why they need an agent |
| 4 | **Agentic Frameworks: LangGraph, CrewAI, Semantic Kernel** | [mem0.ai](https://mem0.ai/blog/agentic-frameworks-ai-agents) | • Semantic Kernel = .NET-first agentic framework (YOUR stack) • LangGraph = state machine approach, good for complex branching • CrewAI = multi-agent "crew" with roles (planner, analyst, critic) • Best for: choosing the right framework for ArNir + UpworkAgent OS |

---

## 🎥 YouTube Video (Long Form)

| # | Title | Link | Summary |
|---|-------|------|---------|
| 1 | **AI Agents vs AI Chatbots — Difference Explained** | [youtube.com](https://www.youtube.com/watch?v=qzkQqNfIKwY) | • Visual breakdown of chatbot vs agent architecture • Shows ReAct loop in action with real examples • Explains why agents are the future of business automation • Best for: watching before pitching agent solution to a client |

---

## 📱 YouTube Short

| # | Title | Link | Summary |
|---|-------|------|---------|
| 1 | **Agentic AI — Agent Workflows: Memory, Tools, Planning** | [medium.com](https://medium.com/@lovelyndavid/agentic-ai-introduction-ec1e6f00fad5) | • MCP protocol: how agent communicates with tools • Short-term memory (RAM) vs long-term memory (pgvector) • Reflexion: agent checks own reasoning, revises if wrong • Best for: 5-min read showing you already understand all 3 components |

> ⚠️ Dedicated short videos on agentic AI tend to be hype. Read the FreeCodeCamp handbook above — it's the most practical non-hype resource.

---

## 🔧 Framework Selection Guide (.NET Dev Edition)

| Framework | Language | Best For | ArNir Fit? |
|-----------|----------|----------|------------|
| **Semantic Kernel** | C# / .NET | Azure + Microsoft stack | ✅ YES — your stack |
| LangChain | Python | Quick prototyping, RAG | ⚠️ Python only |
| LangGraph | Python | Complex branching flows | ⚠️ Python only |
| CrewAI | Python | Multi-agent teams | ⚠️ 3× token cost |
| n8n | No-code | Workflow automation | ✅ You use daily |

**Recommendation for ArNir:** Semantic Kernel + pgvector already in place = 80% of agent infrastructure done.

---

## 🏢 Real Business Use Cases

| Business | Chatbot Version | Agent Version |
|----------|----------------|---------------|
| Restaurant | "What's on the menu?" | "Find best dish for anniversary dinner under $50, check table availability, suggest wine pairing" |
| Legal firm | "What does clause 4 say?" | "Find clause, compare with CRM contract terms, flag discrepancy, draft amendment" |
| E-commerce | "Where is my order?" | "Track order, detect delay, notify customer, offer discount, update CRM" |
| HR | "What is leave policy?" | "Check employee leave balance, check team calendar, auto-approve if no conflict" |
| ArNir client | "What was discussed?" | "Find relevant meetings, summarize decisions, flag pending actions, create Notion task" |

---

## 💡 ArNir Upgrade Path (Chatbot → Agent)

```
TODAY (Chatbot):
User question → RAG → LLM → Answer

NEXT (Agent):
User goal
  → Router classifies intent (T4 pattern)
  → Planner breaks into steps
  → Tool 1: pgvector RAG search
  → Tool 2: PDF document search  
  → Tool 3: External API (CRM, calendar)
  → Memory: store results in pgvector
  → LLM reasons: goal achieved? Y/N
  → Output: goal completed

Infrastructure already in ArNir:
✅ pgvector = memory layer
✅ RAG = Tool 1
✅ LLM calls = planner
❌ Missing: tool registry + ReAct loop wiring
   → Semantic Kernel adds this in .NET
```

---

## ✅ After Reading Checklist

- [ ] Can define agent vs chatbot in 2 sentences to a client
- [ ] Know 3 components: Planner + Tools + Memory
- [ ] Understand ReAct = LLM decides flow, not your code
- [ ] Know Semantic Kernel = .NET-native agent framework
- [ ] Can identify which ArNir pieces are already agent-ready
- [ ] Have a real consulting pitch: chatbot vs agent ROI story
- [ ] Know 4 reasoning patterns: ReAct, Reflexion, Plan-Execute, Tree of Thoughts

---

## 🎓 P00 Complete — What You Now Know

```
T1: AI/ML/DL/GenAI map           → Can explain to any client
T2: Tokens/Context/RAG           → Can calculate + optimize costs
T3: Attention mechanism          → Understand why RAG+Attention works
T4: API calls + parameters       → Can build + tune production API layer
T5: Agent mental models          → Can design + pitch agent solutions
```

**Next Phase:** P01 — Prompt Engineering
*"You use prompts daily. Now learn WHY some work and others don't."*

---

## 🔗 Related

- Previous: `p00-topic-04-resources.md`
- Next Phase: `02-learning/phase-P01/`
- ADR: `00-system/decisions/ADR-003-resource-format.md`
