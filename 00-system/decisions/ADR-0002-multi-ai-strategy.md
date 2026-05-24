# ADR-0002 — Multi-AI Platform Strategy
DATE=2026-05-24
STATUS=ACCEPTED

## Decision
GitHub = SSOT. AI platforms = stateless engines. Never trust platform memory.

## Why
Platform memory unreliable, not portable, not versioned.
GitHub = versioned, portable, persistent, AI-readable.

## Platform Roles
- Claude → primary tutor, coding, file creation
- ChatGPT → secondary, research, alternative explanations
- Gemini → long-context sessions (1M token window)
- Perplexity → targeted research lookups only

## Handoff Protocol
See AI-HANDOFF/ folder for platform-specific prompts.

## Impact
Every session ends with git commit. No exceptions.
