# memory-rules.md
VERSION=2.0

## Golden Rule
NEVER trust platform memory (Claude/GPT/Gemini/Perplexity).
GitHub = only source of truth.

## Session Start Protocol
1. Load NEXT-SESSION.md (one file, all context)
   → web_fetch: https://raw.githubusercontent.com/pankildesai1988/AgenticAI/main/NEXT-SESSION.md
2. Confirm resume point aloud: "You are on P[X]-T[NN]. CUT_POINT: [value]. Next: [NEXT_STEP]"
3. Apply rules from NEXT-SESSION.md RULES section
4. Then begin

## Session End Protocol
1. AI generates FULL updated NEXT-SESSION.md content (all fields)
2. Announce: "Session end. Copy NEXT-SESSION.md block below. Commit via Claude Code."
3. List resource files pending git commit
4. User commits: `git commit -m "feat(P[XX]): [what was done]"`
5. git push

## Session Break Protocol (mid-topic)
When session must end before topic completes:
1. Fill CUT_POINT field precisely: "P[XX]-T[NN]: Covered [A]. NOT YET [B]. Next: [first action]."
2. Generate NEXT-SESSION.md with PHASE_STATUS=IN_PROGRESS
3. Commit before closing

## Compression Schedule
| Trigger | Action |
|---------|--------|
| Every 5 sessions | Compress snapshots → compressed-memory/ |
| Phase complete | Collapse WHAT PANKIL KNOWS: 5 topic lines → 1 summary line per phase |
| Roadmap mutation | Log in roadmap-status.md mutation table |
| Tool dropped | Update tooling-state.md |

## Phase Collapse Rule (NEXT-SESSION.md size control)
When phase completes, replace its 5 topic lines with:
`- P[XX]: [Phase Name] ✅ ([keyword], [keyword], [keyword])`
Example: `- P00: AI Foundation ✅ (foundation map, tokens/RAG, attention, API cost, agent mental models)`
Current phase topics stay expanded. File target: ≤ 150L always.
