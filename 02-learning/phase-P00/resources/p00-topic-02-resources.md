# P00 · Topic 2: How LLMs Work
**Phase:** P00 AI Foundation  
**Status:** Reference material — use AFTER completing Topic 2 learning  
**Last Updated:** 2026-05-25  
**Rule:** Generated after topic completed. Web-fetched for freshness.

---

## 🗺️ The Map (Quick Recap)

```
Your text
   ↓
Tokenizer → sub-word chunks (e.g. "pgvector" → ["pg","vector"])
   ↓
Token IDs → integers (dictionary lookup)
   ↓
Embeddings → high-dim float vectors (~1536 numbers = meaning encoded)
   ↓
LLM processes → predicts next token → response
   ↓
Context Window = total tokens LLM can SEE at once (input + history + output)
   ↓
Overflow → oldest messages dropped silently → hallucination risk
   ↓
Fix = RAG (pgvector retrieves only relevant history chunks)
```

**Key insight from YOUR session:**
> More context ≠ better. 2025 study: all 18 frontier models (GPT-4.1, Claude, Gemini)
> performed WORSE as input grew. Quality of context > quantity.

---

## 📰 Blog / Article

| # | Title | Link | Summary |
|---|-------|------|---------|
| 1 | **Tokens, Embeddings, Context Windows — The LLM Glossary for Web Developers** | [tenxdeveloper.com](https://www.tenxdeveloper.com/blog/tokens-embeddings-context-windows-llm-glossary) | • Uses developer analogies: tokens = bytecode, embeddings = meaning • Practical search example: "MacBook Pro M3" matches "Professional coding laptop" via embeddings • Shows why SQL LIKE fails where embeddings succeed • Best for: .NET devs mapping LLM concepts to familiar patterns |
| 2 | **LLM Context Windows Explained: 4K to 1M Tokens** | [devtk.ai](https://devtk.ai/en/blog/llm-context-window-explained/) | • Context window = invisible boundary every API call has • Input + output + history ALL count toward limit • RAG pattern: retrieve top-K chunks instead of stuffing everything • Best for: understanding why ArNir needs smart context management |
| 3 | **A Guide to Context Engineering for LLMs** | [bytebytego.com](https://blog.bytebytego.com/p/a-guide-to-context-engineering-for) | • Introduces "context engineering" — the discipline of what you put in context • 2025 Chroma study: models drop from 95% → 60% accuracy as input grows • Shows what fits in context window: system prompt + history + RAG docs + query • Best for: senior devs building production LLM apps |
| 4 | **How LLMs Work: Tokens, Embeddings, and Transformers** | [dremio.com](https://www.dremio.com/blog/how-llms-work-tokens-embeddings-and-transformers/) | • Full pipeline explained with visuals • Embeddings = position in multi-dimensional meaning-space • Closer vectors = closer meaning (the math behind pgvector) • Best for: understanding WHY vector similarity search works |

---

## 🎥 YouTube Video (Long Form)

| # | Title | Link | Summary |
|---|-------|------|---------|
| 1 | **Transformers Step-by-Step Explained** | [youtube.com](https://www.youtube.com/watch?v=avjX3QrYkls) | • Full transformer pipeline: tokens → embeddings → attention → output • Step-by-step with visual diagrams • Covers positional encoding (how LLM knows word order) • Best for: 45-min deep dive after mastering token basics |

---

## 📱 YouTube Short

| # | Title | Link | Summary |
|---|-------|------|---------|
| 1 | **How Attention Mechanism Works #LLM #embedding** | [youtube.com](https://www.youtube.com/watch?v=KMHkbXzHn7s) | • 60-sec visual of attention weights • Shows which tokens "light up" for a given word • Good bridge between Topic 2 and Topic 3 • Best for: quick visual before reading the deep articles |

---

## 📘 Substack / Newsletter

| # | Title | Link | Summary |
|---|-------|------|---------|
| 1 | **Understanding LLM Context Windows: Tokens, Attention, Challenges** | [medium.com](https://medium.com/@tahirbalarabe2/understanding-llm-context-windows-tokens-attention-and-challenges-c98e140f174d) | • Explains "lost in the middle" problem — key info buried in long context = model struggles • Context window = working memory analogy • Safety note: longer context = bigger attack surface for prompt injection • Best for: understanding ALL risks, not just hallucination |

---

## 🏢 Real Business Use Cases

| Scenario | Problem | LLM Concept Used |
|----------|---------|-----------------|
| ArNir long conversation loses context | User asks about "that budget" — LLM forgot | Context window + RAG fix |
| Customer support bot gives wrong answer | Old chat history dropped, new answer contradicts | Sliding window / RAG |
| E-commerce search: "laptop for coding" | SQL LIKE fails, no keyword match | Embeddings + vector similarity |
| Legal doc: find relevant clauses | 500-page doc won't fit context | RAG chunking + map-reduce |
| Multi-language chatbot | New words tokenized as sub-words | Sub-word tokenization |

---

## 💡 ArNir-Specific Notes

```
pgvector you built = embedding store
When user asks → convert question to embedding → cosine similarity search
→ retrieve top-K relevant past messages
→ inject ONLY those into messages[] 
→ context stays small, accurate, no hallucination

This is production-grade RAG. You built it. Now you know WHY it works.
```

---

## ✅ After Reading Checklist

- [ ] Can explain token vs embedding difference
- [ ] Know why sub-word tokenization handles unknown words
- [ ] Understand context window = hard limit (input + output + history)
- [ ] Know why MORE context can HURT accuracy (Chroma 2025 study)
- [ ] Know RAG = quality context management, not just memory
- [ ] Can explain context window to a client using "filing cabinet" analogy

---

## 🔗 Related

- Previous: `p00-topic-01-resources.md`
- Next: `p00-topic-03-resources.md`
- ADR: `00-system/decisions/ADR-003-resource-format.md`
