# Concrete lifecycle gaps in the research assistant

Three real gaps found in `ResearchChat.tsx` — these are the next teachable targets (build-heavy, each ~20 min).

1. **The `stopped` state is undesigned.** `stop()` is wired to the Stop button, but the turn is only rendered richly while `inFlight` (`isLast && busy`). After stop, `busy` → false, and the non-inFlight branch only renders `phase === 'done'` or `'error'`. A turn stopped mid-`searching`/`streaming-answer` collapses to just the user's question — **partial work vanishes, no "stopped" marker, no Continue/Regenerate.** This is the clearest gap and a perfect micro-lesson.

2. **Retry duplicates instead of regenerating in place.** `retryQuestion → send(question)` appends a *new* user turn. After an error, the failed turn's banner stays and the question appears twice. `regenerate()` (from `useChat`) would retry the last turn in place.

3. **Transport-error text may leak raw messages.** The bottom `ErrorBanner` renders `error.message` directly (no friendly-message mapping), so a network/fetch error can surface technical text.

These define Phase 2's next few lessons. Start with the stopped state.
