# Legible wait micro-states shipped

The learner implemented `deriveInFlightPhase` with distinct `SubmittedAck` and `ThinkingGap` indicators, refactored the in-flight turn branch to key on wait phase instead of raw `research` presence, and added auto-scroll on send with a near-bottom scroll button. The silent thinking gap and misleading "Working…" during `submitted` are closed.

**Evidence:** user reported lesson 4 complete; code review confirms `lib/derive-in-flight-phase.ts`, wait-phase render branch, `SubmittedAck`/`ThinkingGap`, and scroll container + `lastTurnRef`/`bottomRef`/`showScrollButton` in `ResearchChat/index.tsx`.

**Implications:** perceived-latency lever #1 (legible progress) is in place. Next arc is **trust signals** — the brief already has source pills and a raw `confidence` enum in the footer, but nothing scannable above the fold and no calibrated uncertainty copy.
