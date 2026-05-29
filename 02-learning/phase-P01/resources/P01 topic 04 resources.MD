# P01 · Topic 4: Prompt Engineering for ArNir (Production Prompts)
**Phase:** P01 Prompt Engineering
**Status:** Reference material — use AFTER completing Topic 4 learning
**Last Updated:** 2026-05-29
**Rule:** Generated after topic completed. Web-fetched for freshness.

---

## 🗺️ The Map (Quick Recap)

```
T1 → Prompt anatomy (Role/Context/Task/Format/Constraints)
T2 → Patterns (zero-shot / few-shot / CoT)
T3 → System prompts + temperature + model selection
T4 → THIS: Apply all of it to real ArNir production build
```

**What shipped this session:**
```
RAG answer alone          →  client: "how do I know it's right?"
RAG + PDF viewer + highlight →  client: "I can see exactly where it came from"

Trust gap = closed.
Hallucination risk = visible + auditable.
Demo differentiator = built.
```

**Production prompt → production feature pipeline:**
```
System prompt (5-part)
  → RAG retrieval (pgvector top-K)
  → LLM answers (JSON format enforced)
  → page_number + bbox returned
  → PDF.js opens at correct page
  → Canvas overlay highlights bbox
  → Confidence badge (HIGH/MEDIUM/LOW) shown
```

**PdfPig upgrade (text → positioned chunks):**
```csharp
// BEFORE: text only
page.GetWords() → string text

// AFTER: text + position
DocstrumBoundingBoxes.Instance.GetBlocks(words)
  → block.BoundingBox.BottomLeft.X/Y
  → block.BoundingBox.Width/Height
  → stored with page_number in pgvector table
```

**PDF.js highlight pattern:**
```javascript
// After answer received from API:
const { page_number, bbox } = apiResponse;
pdfViewer.goToPage(page_number);
// Draw canvas overlay at bbox coordinates
ctx.fillStyle = 'rgba(255, 255, 0, 0.4)';
ctx.fillRect(bbox.x1, bbox.y1, bbox.x2 - bbox.x1, bbox.y2 - bbox.y1);
```

---

## 📰 Blog / Article

| # | Title | Link | Summary |
|---|-------|------|---------|
| 1 | **How to Add Highlight Annotations to PDFs in JavaScript** | [nutrient.io](https://www.nutrient.io/blog/how-to-add-highlight-annotations-to-pdfs-in-javascript/) | • PDF.js = HTML overlay highlights (free, no save-to-PDF). Commercial SDKs = embedded annotations (persistent) • Yellow rectangle 50% opacity = standard visual for RAG source highlight • For demos: PDF.js canvas overlay is fastest path, no API key needed • Best for: understanding PDF highlight options before choosing approach |
| 2 | **PdfPig API — Bounding Box Extraction** | [products.documentprocessing.com](https://products.documentprocessing.com/parser/net/pdfpig/) | • PdfPig excels at precise positional data per text element (word/block level bbox) • DocstrumBoundingBoxes = block segmenter, NearestNeighbourWordExtractor = word extractor • Use cases: table detection, form processing, content region analysis (RAG highlight = same pattern) • Best for: reference when upgrading text-only PdfPig → positioned extraction |
| 3 | **PdfPig GitHub — Extracting Text with Bounding Box** | [github.com/UglyToad/PdfPig/discussions/374](https://github.com/UglyToad/PdfPig/discussions/374) | • Community discussion showing exact code for chunk + coordinate extraction • GAP parameter (0.3 default) controls word spacing detection — tune for font size • Works for left-to-right and right-to-left scripts • Best for: copy-paste reference when implementing positioned PdfPig extraction |
| 4 | **Prompt Engineering Best Practices for Production RAG** | [palantir.com](https://www.palantir.com/docs/foundry/aip/best-practices-prompt-engineering) | • Production RAG system prompts: constrain to source only + explicit "not found" fallback • Few-shot examples in system prompt anchor JSON output format reliably • Feedback loop: if model misunderstands format → adjust wording → re-test → never guess • Best for: hardening ArNir system prompt for enterprise client deployments |

---

## 🎥 YouTube Video (Long Form)

| # | Title | Link | Summary |
|---|-------|------|---------|
| 1 | **Building RAG with Source Attribution — LlamaIndex** | [learnprompting.org](https://learnprompting.org) | • Shows RAG pipeline: retrieval → answer → source citation in full • Covers chunk metadata strategy: always store page, section, coordinates • Key: source attribution = trust layer. Without it, RAG is a black box to non-technical users • Best for: 1-hr deep dive on production RAG with full auditability pattern |

---

## 📱 YouTube Short / Quick Reference

| # | Title | Link | Summary |
|---|-------|------|---------|
| 1 | **PDF.js Viewer Setup in 5 Minutes** | [pdfjs.express](https://pdfjs.express/) | • PDF.js via CDN = fastest demo setup (no install, no API key) • 26 annotation types available including text highlight, shapes, comments • Customize UI: remove features, match client branding for white-label demos • Best for: quick PDF.js setup before first ArNir demo |

---

## 🏢 Real Business Use Cases

| Industry | Query | ArNir Response |
|----------|-------|---------------|
| Healthcare | "Recommended dosage for metformin?" | Answer + highlight on clinical guideline page 12 |
| Legal | "What does clause 4 say about termination?" | Extract + highlight clause 4 bbox in contract PDF |
| Finance | "What was Q3 revenue?" | Answer + highlight on financial report table page 8 |
| HR | "What is the remote work policy?" | Answer + highlight on employee handbook page 23 |
| E-commerce | "What is the return window for electronics?" | Answer + highlight on policy PDF page 3 |

**Demo pattern (works for ALL industries):**
> Upload industry doc → ask question → show answer + highlight → close trust gap in 30 seconds

---

## 💡 ArNir Production System Prompt (shipped version)

```
You are ArNir, enterprise document assistant for {{CompanyName}}.

CONTEXT:
Answer ONLY from document chunks provided below.
Do NOT use general knowledge. Do NOT guess.
Document chunks: {rag_chunks}

RULES:
- If answer not in chunks → return: "Not found in uploaded documents."
- Never hallucinate dates, numbers, names, or figures.
- Always cite: source filename + page number.
- If answer involves chart or table → say: "See [chart/table] on page X of [filename]."

TONE: Professional. Concise. Consultant-level.

FORMAT (valid JSON only — no markdown fences):
{
  "answer": "...",
  "confidence": "high|medium|low",
  "source": "filename.pdf",
  "page_number": <int>,
  "bbox": { "x1": <float>, "y1": <float>, "x2": <float>, "y2": <float> },
  "chunk_type": "text|table|image"
}
```

---

## 💡 Consulting Pitch — ArNir Document Q&A

**The trust gap pitch:**
> "Every RAG system gives you an answer. ArNir shows you the proof.
> When ArNir answers your clinical question, it opens the source guideline
> and highlights the exact sentence it used. Your team verifies in seconds.
> No hallucination risk. Full audit trail. This is what enterprise AI looks like."

**ROI framing:**
> "One missed clinical detail = liability. One wrong contract clause = lawsuit.
> The highlight layer isn't a nice-to-have. It's your legal defense."

---

## 🔧 Architecture Reference

```
DocumentChunks table (pgvector):
  id, document_id, text, embedding (vector),
  page_number, bbox_x1, bbox_y1, bbox_x2, bbox_y2, chunk_type

RAG query flow:
  1. Embed user query → float[]
  2. pgvector cosine similarity → top-K chunks
  3. Inject chunks into system prompt
  4. LLM returns JSON (answer + confidence + page + bbox)
  5. Frontend: PDF.js open at page_number, draw bbox highlight

Confidence mapping:
  retrieval_score > 0.85 → HIGH
  retrieval_score 0.65–0.85 → MEDIUM
  retrieval_score < 0.65 → LOW
```

---

## ✅ After Reading Checklist

- [ ] Know why trust gap exists in RAG demos (text answer ≠ proof)
- [ ] Understand bbox = bridge between pgvector chunk and PDF viewer
- [ ] Know PdfPig bbox extraction: DocstrumBoundingBoxes + NearestNeighbourWordExtractor
- [ ] Know PDF.js canvas overlay pattern for highlight (no commercial SDK needed)
- [ ] Can explain confidence badge to non-technical client
- [ ] Have production system prompt with JSON format + bbox output
- [ ] Know demo script: upload → ask → highlight → close trust gap
- [ ] Understand next extension: same pattern → ecommerce + finance demos

---

## 🔗 Related

- Previous: `p01-topic-03-resources.md`
- Next: `p01-topic-05-resources.md` (Prompt evaluation + iteration)
- Project file: `07-projects/arnir/arnir-document-qa-feature.md`
- ADR: `00-system/decisions/ADR-0005-resource-format.md`