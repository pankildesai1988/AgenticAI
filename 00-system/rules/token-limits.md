# token-limits.md
VERSION=1.0

## Hard Limits
| File | Max Lines | Max Tokens | On Breach |
|------|-----------|-----------|-----------|
| CLAUDE.md (root) | 200 | ~3k | Split → CLAUDE-EXT.md |
| skill.md | 500 | ~8k | Split → skill-part2.md |
| current-state.md | 100 | ~1.5k | Archive → learning-state/ |
| roadmap-status.md | 150 | ~2.5k | Archive old mutations |
| active-focus.md | 80 | ~1.2k | Sprint-scoped only |
| Phase files | 400 | ~6k | Split → -part2.md |
| Session snapshots | 150 | ~2.5k | New file per session |

## Compression Rule
Every 5 sessions:
  raw session-snapshots/ → summarize → compressed-memory/
  Format: compressed-YYYY-MM-[range].md
  Keep: key insights, decisions, analogies that clicked
  Drop: raw Q&A, verbose explanations

## Context Load Order (selective injection)
1. current-state.md (always)
2. roadmap-status.md (always)
3. active-focus.md (always)
4. current phase file (always)
5. tooling-state.md (only if tool question)
6. relevant arch doc (only if design question)
7. compressed-memory (only if continuity needed)
NEVER load all files at once.
