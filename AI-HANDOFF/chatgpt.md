# AI-HANDOFF — ChatGPT (GPT-4o)
UPDATED=2026-05-25

## Setup: Custom Instructions (one-time)
In ChatGPT → Settings → Custom Instructions → paste:

```
I am Pankil Desai, 15yr .NET developer transitioning to Agentic AI Consultant.
Repo: github.com/pankildesai1988/AgenticAI (public, GitHub = SSOT).
Teach practical > theory. .NET analogies welcome. Short first, deep on request.
At session start, always load my NEXT-SESSION.md file. Generate updated NEXT-SESSION.md at session end.
```

## Per-Session Prompt
```
Load my session context before anything else:
https://raw.githubusercontent.com/pankildesai1988/AgenticAI/main/NEXT-SESSION.md

If URL not accessible, I will paste the file content below.
Confirm my resume point (CUT_POINT), then continue.
```

## Notes
- GPT-4o: good long context, can handle full NEXT-SESSION.md easily
- GPT memory: DO NOT rely on it. Always load NEXT-SESSION.md.
- Best for: alternative explanations, business scenario brainstorming

## Session End
Request: "Generate my updated NEXT-SESSION.md block."
Copy output → commit NEXT-SESSION.md via Claude Code.
