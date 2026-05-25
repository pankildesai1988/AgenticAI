# P00 · Topic 4: First API Call — Parameters, Cost & Router Pattern
**Phase:** P00 AI Foundation  
**Status:** Reference material — use AFTER completing Topic 4 learning  
**Last Updated:** 2026-05-25  
**Rule:** Generated after topic completed. Web-fetched for freshness.

---

## 🗺️ The Map (Quick Recap)

```json
// API Call Anatomy — What You Now Understand
{
  "model": "gpt-4",
  "messages": [
    {"role": "system",    "content": "You are..."},   // instructions
    {"role": "user",      "content": "Hello"},         // user input
    {"role": "assistant", "content": "Hi!"},           // past response
    {"role": "user",      "content": "What is RAG?"}  // new question
  ],
  "max_tokens": 1000,    // OUTPUT cap only. Input billed separately.
  "temperature": 0.7     // 0=deterministic, 1=creative. NOT returned in response.
}
```

**Key cost formula learned this session:**
```
Daily Cost = (Input tokens per call × Daily sessions × Price per 1K) / 1000
                                    +
             (Output tokens per call × Daily sessions × Price per 1K) / 1000

RAG reduces input tokens ~80% → cost drops ~80%
```

**Router Agent pattern you designed:**
```csharp
float temperature = requestType switch {
    "factual_qa"    => 0.1f,   // RAG: match data exactly
    "creative_copy" => 0.8f,   // Product descriptions: creative
    "code_gen"      => 0.2f,   // Code: mostly deterministic
    "chat"          => 0.7f,   // Conversation: natural
    _ => 0.5f
};
```

---

## 📰 Blog / Article

| # | Title | Link | Summary |
|---|-------|------|---------|
| 1 | **LLM Parameters: Temperature, Top-P, Top-K Complete Guide 2026** | [amirteymoori.com](https://amirteymoori.com/llm-parameters-explained-temperature-top-p-top-k/) | • All key parameters with recommended values per use case • Model-specific tips: Claude Sonnet 200K tokens, GPT-4o 128K • Max tokens reference table: Q&A=50-150, code=500-1500, articles=1000-2000 • Best for: bookmarking as parameter cheat-sheet for ArNir |
| 2 | **Temperature, Top-P, and LLM Settings Explained** | [llmguides.ai](https://llmguides.ai/learn/llm-settings-explained/) | • Plain language, no math • Key rule: set max_tokens to 1.5× expected response length • Cost control: max_tokens prevents "runaway responses" that burn budget • Best for: sharing with junior devs on your team |
| 3 | **Token Optimization and Cost Management for ChatGPT & Claude** | [intuitionlabs.ai](https://intuitionlabs.ai/articles/token-optimization-chatgpt-claude-costs) | • Real stat: simple 3-word input cost $0.0018 on message 1, $2.41 by message 260 (hidden token tax) • OpenAI spends "tens of millions" on polite niceties ("thank you", "please") • Chunking + RAG = business-critical, not micro-optimization • Best for: showing clients WHY cost management matters |
| 4 | **LLM Parameters Explained — Practical Guide with Python Examples** | [learnprompting.org](https://learnprompting.org/blog/llm-parameters) | • All 6 parameters: temperature, top-p, max_tokens, frequency_penalty, presence_penalty, stop sequences • Code examples for each • When to use frequency_penalty: stops repetitive AI responses in long convos • Best for: copy-paste reference when building ArNir API layer |

---

## 🎥 YouTube Video (Long Form)

| # | Title | Link | Summary |
|---|-------|------|---------|
| 1 | **LLM Temperature, Top-P, Top-K & 11 Core Parameters — Complete Guide** | [amitray.com](https://amitray.com/llm-parameters-temperature-top-p-top-k-guide/) | • Covers all 11 parameters with code for GPT, Claude, Gemini, Llama • Downloadable cheat sheet for creative/coding/RAG use cases • 85% of production apps use at least 3 parameters — most devs use defaults blindly • Best for: 1-hour deep dive before finalizing ArNir API architecture |

---

## 📱 YouTube Short / Quick Reference

| # | Title | Link | Summary |
|---|-------|------|---------|
| 1 | **Temperature Settings Explained Quick** | [freeacademy.ai](https://freeacademy.ai/blog/llm-parameters-temperature-top-p-top-k-max-tokens) | • Warning: never set temperature >1.3 — output becomes incoherent • "max_tokens too low" = most common beginner mistake • Try OpenAI Playground to see temperature effects live • Best for: quick experiment before reading full guide |

---

## 💰 Cost Comparison Table (2026 Prices)

| Model | Input (per 1M tokens) | Output (per 1M tokens) |
|-------|----------------------|------------------------|
| Claude Haiku 4.5 | $1 | $5 |
| Claude Sonnet 4.6 | $3 | $15 |
| Claude Opus 4.6 | $15 | $75 |
| GPT-4o | ~$2.50 | ~$10 |

**ArNir recommendation:** Haiku for RAG retrieval + classification. Sonnet for final response generation.

---

## 🏢 Real Business Use Cases

| Scenario | Parameter Strategy | Saving |
|----------|-------------------|--------|
| Restaurant chatbot, 500 users/day | RAG → 1050 tokens/call instead of 5500 | 80% cost cut |
| ArNir multi-tenant | Router Agent → temp 0.1 for Q&A, 0.8 for creative | Quality + cost |
| Legal document review | max_tokens=300, temp=0.1 | Precise, no rambling |
| Marketing copy generator | temp=0.8, max_tokens=500 | Creative, controlled length |
| Code review bot | temp=0.2, max_tokens=1000 | Consistent, thorough |

---

## 💡 ArNir-Specific Implementation Notes

```csharp
// Production-ready API call pattern for ArNir
// Always log usage for cost tracking
var response = await openAI.ChatCompletions.CreateAsync(new() {
    Model = "gpt-4",
    Messages = messages,         // RAG-filtered, not full history
    MaxTokens = GetMaxTokens(requestType),
    Temperature = GetTemperature(requestType)
});

// ALWAYS capture this — your cost dashboard
var usage = response.Usage;
await LogApiUsage(new ApiUsageLog {
    PromptTokens = usage.PromptTokens,
    CompletionTokens = usage.CompletionTokens,
    TotalTokens = usage.TotalTokens,
    RequestType = requestType,
    UserId = userId,
    Timestamp = DateTime.UtcNow
});
// Temperature NOT in response — log what YOU sent
```

---

## ✅ After Reading Checklist

- [ ] Know max_tokens = OUTPUT only, input billed separately
- [ ] Can calculate daily API cost from scratch
- [ ] Know temperature range: 0=deterministic, 1=creative
- [ ] Can design Router Agent for different request types
- [ ] Understand usage object in API response for cost tracking
- [ ] Know prompt caching exists (next level cost saving for ArNir)
- [ ] Can pitch "80% cost reduction" to a client with real numbers

---

## 🔗 Related

- Previous: `p00-topic-03-resources.md`
- Next: `p00-topic-05-resources.md`
- ADR: `00-system/decisions/ADR-003-resource-format.md`
