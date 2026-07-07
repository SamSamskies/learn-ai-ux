# Response lifecycle: already handled well; new floor set

Reviewed the real research-assistant code (`learnopenai/research-assistant`, `components/ResearchChat.tsx` + `lib/research-state.ts`). The learner has **already implemented most of the response lifecycle to a high standard** — this raises the floor for Phase 2.

Evidence of genuine understanding (not just coverage):
- **idle** → `EmptyState` with a Wayfinder prompt ("What are you researching?" + gentle suggestions).
- **submitted/thinking** → doesn't rely on `status` alone; streams a custom `data-research` part with a domain `phase` (`searching | streaming-answer | done | error`) and renders **labeled steps** ("Searching the web…", "Searching documents…") plus a skeleton card. This is the advanced "stream the steps, not just tokens" pattern I was going to teach — he's already doing it.
- **streaming** → progressive render of the structured brief via `BriefPreviewPanel` while `phase === 'streaming-answer'`.
- **complete** → `BriefArticle` with sources, confidence, grounding disclosure, Copy button (Trust Builder patterns present).
- **error** → two paths (domain `phase === 'error'` and transport `error`), both with friendly fallback + retry.

Implication: skip the Lesson 0001 baseline. The real zone of proximal development is the **gaps** (see LR-0003) — the undesigned stopped/interrupted state, retry-in-place vs. duplicate-question, and raw transport-error text. Teach those next.
