# Working Notes

## Learner preferences
- **Lesson shape:** short concept explainer → hands-on build in a real repo. Build-heavy, not quiz-heavy.
- **Lesson size:** ~20 min, one tangible win each.
- **Stack:** Vercel AI SDK + Next.js/React.
- Strong hands-on learner — Phase 1 was a long series of "build X, then ship it" records. Lean into that.

## Established prior knowledge (as of session 1)
- Phase 0 complete: Cursor power user (26 learning records in `learncursor`).
- Phase 1 complete: OpenAI platform (37 records in `learnopenai`) — Responses API, streaming, streaming tool calls, structured outputs, prompt caching, MCP, image gen.
- Already brushed Phase 2 concepts in Phase 1: a **streaming UI state machine** (LR-0019), a **research assistant with streaming UI** (LR-0030), **AI SDK server integration** (LR-0034), and an **AI-native design track** with Stitch design-to-code (LR-0035–0037).
- Implication: do NOT re-teach "what is streaming." Start at the *design framework* level and elevate his existing mechanics into deliberate UX decisions.

## Retrofit target
- The Phase 1 **research assistant** is the project we're improving throughout Phase 2.
- Repo: `github.com/SamSamskies/learnopenai/tree/main/research-assistant` (Next.js App Router). Main component: `components/ResearchChat.tsx`. Custom streaming: server emits a `data-research` UI-message part carrying `ResearchUIState` (`lib/research-state.ts`), read via `lib/read-research-stream.ts`. Uses `useChat` from `@ai-sdk/react` + `DefaultChatTransport`. Tailwind w/ Material-ish design tokens. **TODO:** confirm whether he has this cloned locally in a path I can edit, or if lessons should stay code-snippet-based.
- Notable: he already streams *labeled steps* + progressive structured output — more advanced than the Lesson 0001 baseline.

## Open threads
- Is the research-assistant repo cloned locally somewhere I can edit directly? (Currently only reading it from GitHub.)
- Decide whether he wants AI Elements (Vercel's prebuilt AI components) or hand-rolled components for the retrofit.
