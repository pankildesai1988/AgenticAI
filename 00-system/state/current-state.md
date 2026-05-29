# Current State
<!-- SSOT. Max 100 lines. Update every session end. -->

STATE_VERSION=v9
LAST_UPDATED=2026-05-29
LAST_AI=Claude (claude.ai chat, caveman/ultra)
CURRENT_PHASE=P01
PHASE_STATUS=IN_PROGRESS
NEXT_ACTION=Start P01-T5 — Prompt evaluation + iteration + consultant delivery
BLOCKER=None
OVERALL_PROGRESS=40% (P00 complete + P01 80% complete)
SESSION_BOOTSTRAP=NEXT-SESSION.md (ADR-0006)

## What Was Done This Session
- P01-T4: ArNir production prompts — designed + shipped full feature
- ArNir Doc Q&A: PDF inline viewer + source highlight (healthcare demo complete)
- PdfPig upgraded: text-only → positioned chunks (bbox per block via DocstrumBoundingBoxes)
- pgvector schema extended: page_number + bbox columns added to DocumentChunks
- RAG response extended: JSON now includes page_number + bbox + chunk_type
- PDF.js viewer: side panel, auto-jump to page, canvas overlay highlight
- Confidence badge: HIGH/MEDIUM/LOW from retrieval_score
- CORS env var fix applied
- Tests: 76/76 backend + 37/37 frontend shared + 13/13 healthcare ✅
- 07-projects/ folder created. First project note committed.

## Pankil's Current Understanding Level
- Prompt anatomy (4 parts): ✅
- Zero-shot / few-shot / CoT: ✅
- System prompt 5-part + 9 tones + temperature: ✅
- Production prompt → production feature: ✅ (shipped ArNir T4)
- Prompt evaluation + iteration: ❌ → T5

## ArNir Status
- Healthcare demo: COMPLETE ✅ (upload PDF → ask → highlight → confidence badge)
- System prompt: 5-part, RAG-only, JSON + bbox + confidence
- Tests: all green
- Next: ecommerce + finance demos OR S3/Blob PDF storage

## UpworkAgent OS Status
- Job scoring: CoT + few-shot + reasoning_steps ✅
- Proposal prompt v2: 7 fixes applied ✅
- PENDING: 1 real winning proposal as few-shot example
- PENDING: 7 Python fixes to _draft_with_claude

## Key Insights This Session
- Trust gap = biggest RAG demo blocker. Highlight closes it in 30 seconds.
- bbox = bridge: pgvector metadata → PDF.js canvas overlay. Same coordinates.
- Confidence badge = non-technical client signal. HIGH/MEDIUM/LOW they understand.
- Demo script: upload → ask → highlight → "verify every answer in seconds"
- 07-projects/ = new folder for shipping notes (not learning resources)