# ADR-0005: Learning Resource File Format

**Date:** 2026-05-24
**Status:** Accepted
**Decided By:** Pankil + Claude (Session)

---

## Context

AgenticAI Learning OS needed a standard format for 3rd-party learning resources per topic.
Pankil requested resources be practical, non-tech-person friendly, and multi-platform.

## Decision

- One markdown file per topic (not per phase)
- File naming: `p[XX]-topic-[NN]-resources.md`
- Location: `02-learning/phase-P[XX]/resources/`
- Resources generated ONLY after topic is completed in session
- Web-fetched on day of generation for freshness
- Each resource has: Title + Link + 4-bullet summary
- Platforms covered: Blog, YouTube Video, YouTube Short, Facebook, Instagram, Substack
- Include real business use cases in non-tech language
- Include checklist for self-verification

## Rationale

- One file per topic = easy to find, easy to git diff
- Generated after learning = reinforcement, not pre-reading distraction
- Web-fetched = always current, never stale
- Non-tech summaries = Pankil can share with clients/prospects

## Consequences

- More files in repo (acceptable — each file small)
- Claude must web-search before generating (adds latency, worth it)
- Instagram/Facebook resources often weaker than LinkedIn/Substack for AI topics — noted in each file
