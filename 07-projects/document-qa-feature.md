# ArNir — Document Q&A Feature
PROJECT=ArNir
FEATURE=Document Q&A with PDF Inline Viewer + Highlight
STATUS=COMPLETE ✅
COMMITTED=2026-05-29
DEMO=Healthcare (primary)

---

## What Shipped

PDF inline viewer with source highlighting added to healthcare demo.
Ask question → RAG retrieves answer → Source Documents panel opens PDF
at exact page → yellow highlight over retrieved text.

Confidence badge (HIGH / MEDIUM / LOW) shown on every answer based on
retrieval score. No hallucination. Full audit trail.

## Stack Used
- Backend: ASP.NET Core net9, PdfPig (bbox coordinates), pgvector
- Frontend: PDF.js (browser-native, CDN)
- API: OpenAI / Claude / Gemini (RAG response)
- Storage: DB bytes column (local demo)

## Schema Changes
DocumentChunks table — added columns:
- page_number INT
- bbox_x1, bbox_y1, bbox_x2, bbox_y2 FLOAT
- chunk_type VARCHAR(10) → "text" | "table" | "image"

## API Response Format
```json
{
  "answer": "...",
  "confidence": "high|medium|low",
  "source": "filename.pdf",
  "page_number": 3,
  "bbox": { "x1": 72.0, "y1": 450.0, "x2": 540.0, "y2": 510.0 },
  "chunk_type": "text"
}
```

## Test Results
- Backend: 76/76 ✅
- Frontend shared: 37/37 ✅
- Frontend healthcare: 13/13 ✅

## CORS Fix
Applied CORS env var fix. API must run locally:
`dotnet run --launch-profile https` from ArNir.API

## Demo Script (for prospects)
1. Upload medical PDF
2. Ask clinical question
3. Source Documents panel opens → PDF at correct page → yellow highlight
4. Show confidence badge
5. Talking point:
   "ArNir shows exactly where every answer came from.
   Your team can verify in seconds. No hallucination risk. Full audit trail."

## Consulting Value
- Closes trust gap in RAG demos
- Explainability = enterprise requirement (compliance, audit)
- Differentiator vs generic chatbots

## Next Steps
- [ ] Extend to ecommerce + finance demos (same pattern)
- [ ] Replace DB bytes column → S3/Azure Blob for production
- [ ] Add multi-doc highlight (answer spans 2 docs → highlight both)
- [ ] Table/image chunk_type → blue highlight (distinguish from text)