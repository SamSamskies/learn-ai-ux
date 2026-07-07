# Transport errors shipped — lifecycle arc complete

The learner implemented `formatTransportError` with plain-language mapping for network, auth, rate-limit, and server failures, wired it into the transport `ErrorBanner`, and added `retryTransportError` that regenerates in place when an assistant message exists. Every lifecycle exit (done, domain error, stopped, transport error) now has deliberate UI treatment.

**Evidence:** user reported lesson 3 complete; code review of `ResearchChat/index.tsx` and `lib/format-transport-error.ts` confirms mapper and retry pattern match the lesson spec.

**Implications:** lifecycle retrofit is done. Next arc is **perceived latency** — the repo still collapses early wait states and has a silent gap when an assistant message exists but no `data-research` part has arrived yet. Teach `deriveInFlightPhase` + distinct submitted/thinking/working treatments next.
