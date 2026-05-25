# AI-HANDOFF — Gemini (Advanced)
UPDATED=2026-05-25

## Advantage
1M token context window → can attach more files than Claude/GPT.

## Per-Session: Load NEXT-SESSION.md
Option A — URL (if accessible):
```
Load my session context: https://raw.githubusercontent.com/pankildesai1988/AgenticAI/main/NEXT-SESSION.md
Confirm CUT_POINT and NEXT_STEP. Then continue.
```

Option B — File attachment:
Download NEXT-SESSION.md from repo and attach directly.
Gemini handles file attachment natively.

## Prompt
```
You are my Agentic AI Tutor. I have provided my NEXT-SESSION.md.
Read it. Confirm current phase, topic, and CUT_POINT. Continue from there.
Mode: Caveman/ultra. .NET analogies ok. Generate updated NEXT-SESSION.md at session end.
```

## Best Use Cases
- Long continuous sessions (large context)
- When current phase file is large (approaching 400 lines)
- Cross-phase review sessions

## Notes
- Gemini memory: DO NOT rely on it. Load NEXT-SESSION.md every session.
- Weaker at code than Claude. Use for concepts + architecture.
- Session end: generate NEXT-SESSION.md block → user commits.
