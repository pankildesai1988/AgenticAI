# AI-HANDOFF — ChatGPT (GPT-4o)
UPDATED=2026-05-24

## Setup: Custom Instructions (one-time)
In ChatGPT → Settings → Custom Instructions → paste:

```
I am Pankil Shah, 15yr .NET developer transitioning to Agentic AI Consultant.
Repo: github.com/pankildesai1988/AgenticAI (private, GitHub = SSOT).
Teach practical > theory. .NET analogies welcome. Short first, deep on request.
Always read my pasted state files before responding. Generate CONTEXT UPDATE at session end.
```

## Per-Session Prompt
```
Read these state files before anything else:

[PASTE current-state.md]
[PASTE roadmap-status.md]
[PASTE active-focus.md]
[PASTE current phase file]

Confirm my current phase and NEXT_ACTION. Then continue.
```

## Notes
- GPT-4o: good long context, paste all 4 files safely
- GPT memory: DO NOT rely on it. Always paste state files.
- Best for: alternative explanations, business scenario brainstorming

## Session End
Request: "Generate my CONTEXT UPDATE block."
Paste output into current-state.md → commit.
