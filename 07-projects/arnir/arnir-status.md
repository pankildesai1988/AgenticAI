# ArNir — Document Q&A Feature
**Project:** ArNir (Enterprise AI Platform)
**Feature:** PDF Inline Viewer + Source Highlighting
**Status:** ✅ SHIPPED — Healthcare demo complete
**Completed:** 2026-05-29
**Repo:** https://github.com/pankildesai1988/Generative-AI-Demos/tree/main/ArNir

---

## What Was Built

**Problem solved:** RAG answers had no auditability. Client asked "how do I know AI is right?" — no answer.

**Solution shipped:**
```
User asks question
  → RAG retrieves relevant chunks (pgvector)
  → LLM answers with confidence score
  → PDF side panel opens at exact source page
  → Yellow highlight overlaid on retrieved text bbox
  → Client sees PROOF in seconds
```

**Trust gap closed:**
> "When ArNir answers your question, it opens the source document
> and shows you exactly where that answer came from.
> No hallucination. Full audit trail. Verify every answer in seconds."

---

## Stack

| Layer | Tech | Notes |
|-------|------|-------|
| PDF parsing | UglyToad.PdfPig | Upgraded: now captures bbox coords per chunk |
| Chunk storage | pgvector (PostgreSQL) | Added: page_number, bbox_x1/y1/x2/y2, chunk_type |
| PDF viewer | PDF.js (browser-native) | Free, CDN, no API key needed |
| Highlight | HTML canvas overlay | Yellow 40% opacity over bbox coordinates |
| Confidence | HIGH/MEDIUM/LOW badge | Based on pgvector retrieval score |
| API | ASP.NET Core net9 | CORS env var fix applied |

---

## Schema Change (DocumentChunks table)

```sql
-- Added columns to DocumentChunks
ALTER TABLE "DocumentChunks" ADD COLUMN page_number INT;
ALTER TABLE "DocumentChunks" ADD COLUMN bbox_x1 FLOAT;
ALTER TABLE "DocumentChunks" ADD COLUMN bbox_y1 FLOAT;
ALTER TABLE "DocumentChunks" ADD COLUMN bbox_x2 FLOAT;
ALTER TABLE "DocumentChunks" ADD COLUMN bbox_y2 FLOAT;
ALTER TABLE "DocumentChunks" ADD COLUMN chunk_type VARCHAR(10) DEFAULT 'text';
```

---

## PdfPig Extraction Pattern (key code)

```csharp
// Use DocstrumBoundingBoxes for block-level bbox extraction
var wordExtractor = NearestNeighbourWordExtractor.Instance;
var words = wordExtractor.GetWords(letters);
var pageSegmenter = DocstrumBoundingBoxes.Instance;
var textBlocks = pageSegmenter.GetBlocks(words);
var readingOrder = UnsupervisedReadingOrderDetector.Instance;
var orderedTextBlocks = readingOrder.Get(textBlocks);

foreach (var block in orderedTextBlocks)
{
    var bbox = block.BoundingBox;
    // Store: bbox.BottomLeft.X, bbox.BottomLeft.Y, bbox.Width, bbox.Height
    // + page number + chunk text
}
```

---

## RAG Response JSON (production format)

```json
{
  "answer": "...",
  "confidence": "high|medium|low",
  "source": "filename.pdf",
  "page_number": 3,
  "bbox": { "x1": 72.0, "y1": 450.0, "x2": 540.0, "y2": 510.0 },
  "chunk_type": "text|table|image"
}
```

---

## System Prompt (production, in use)

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

## Test Results
- Backend: 76/76 ✅
- Frontend shared: 37/37 ✅
- Frontend healthcare: 13/13 ✅

---

## How to Run (local)

```bash
dotnet run --launch-profile https
# from ArNir.API directory
# API must be running for PDF viewer to load document bytes
```

---

## Demo Script (for prospects)

1. Upload a medical PDF (e.g. clinical guidelines doc)
2. Ask: "What is the recommended dosage for [drug]?"
3. Show: answer appears with HIGH confidence badge
4. Show: PDF side panel opens automatically at correct page
5. Show: yellow highlight over exact source sentence
6. Say: *"Your team can verify every AI answer in seconds. This is enterprise-grade RAG with full auditability."*

---

## Next Steps

| Option | Effort | Value |
|--------|--------|-------|
| Extend to ecommerce + finance demos | Low | High — same pattern, swap docs |
| Productionize PDF storage (S3/Blob) | Medium | High — DB bytes column won't scale |
| Multi-chunk highlight (show all sources) | Medium | Medium — better for complex answers |
| Table/image chunk type highlight (blue) | Low | Medium — visual diff for non-text sources |

---

## Consulting Talking Points

- **Trust gap closed:** "AI answers are auditable. Not a black box."
- **Hallucination proof:** RAG-only, no general knowledge injection
- **Enterprise-ready:** Confidence scoring + source citation on every answer
- **Demo differentiator:** Competitors show text. ArNir shows the source.

---

## Related Files
- System prompt template: `03-prompts/arnir-system-prompt-template.md` (create next)
- Learning context: `02-learning/phase-P01/resources/p01-topic-04-resources.md`
- Session snapshot: `01-memory/sessions/2026-05-29-P01-T4-ArNir-DocQA.md`