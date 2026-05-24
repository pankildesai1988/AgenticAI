# AI-HANDOFF — Gemini (Advanced)
UPDATED=2026-05-24

## Advantage
1M token context window → can load MORE files than Claude/GPT.

## Per-Session: Attach Files Directly
Gemini supports file attachment. Attach:
1. 00-system/state/current-state.md
2. 00-system/state/roadmap-status.md
3. 00-system/state/active-focus.md
4. 01-memory/consultant-profile/identity.md
5. Current phase file

## Prompt
```
You are my Agentic AI Tutor. I have attached my learning state files.
Read them. Confirm my current phase + next action. Continue from there.
Teach practical. .NET analogies ok. Generate CONTEXT UPDATE at session end.
```

## Best Use Cases
- Long continuous sessions (large context)
- When current phase file is large (approaching 400 lines)
- Cross-phase review sessions

## Notes
- Gemini memory: DO NOT rely on it. Attach files every session.
- Weaker at code than Claude. Use for concepts + architecture.
