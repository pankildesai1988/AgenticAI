# ADR-0007: Master Prompt Strategy

DATE=2026-05-27
STATUS=ACCEPTED
DECIDED_BY=Pankil + Claude

## Context
Session-end protocol executed manually each session with inconsistent results.
Need reusable, versioned, evolvable prompt template for session-end operations.

## Decision
Store master operational prompts in 03-prompts/ folder.
Each prompt versioned inside file. Evolve per phase. ADR documents strategy.

## Folder
03-prompts/ → operational prompt templates (not learning resources)
02-learning/ → topic resource files (ADR-0005)

## Evolution Rule
After each phase completes:
- Run master prompt → identify gaps
- Fix prompt → bump VERSION field
- Add row to Version History table
- Commit: chore(prompts): evolve session-end prompt vX.X

## Impact
- 03-prompts/ created (new folder)
- master-session-end-prompt.md = first file
- Future: master-session-start-prompt.md, master-resource-prompt.md