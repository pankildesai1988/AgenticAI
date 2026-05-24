# memory-rules.md
VERSION=1.0

## Golden Rule
NEVER trust platform memory (Claude/GPT/Gemini/Perplexity).
GitHub = only source of truth.

## Session Start Protocol
1. Load: current-state.md + roadmap-status.md + active-focus.md
2. Load: current phase file
3. Confirm state aloud: "You are on P[X], next action: [Y]"
4. Then begin

## Session End Protocol
1. AI generates CONTEXT UPDATE block
2. Update current-state.md
3. Create session-snapshots/SESSION-YYYY-MM-DD-[AI].md
4. git commit -m "session: YYYY-MM-DD [AI] P[X]"
5. git push

## Compression Schedule
| Trigger | Action |
|---------|--------|
| Every 5 sessions | Compress snapshots → compressed-memory/ |
| Phase complete | Create phase-summary in learning-state/ |
| Roadmap mutation | Log in roadmap-status.md mutation table |
| Tool dropped | Update tooling-state.md |
