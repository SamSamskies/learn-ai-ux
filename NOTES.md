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
- Repo: `github.com/SamSamskies/learnopenai/tree/main/research-assistant` (Next.js App Router). Main component: `components/ResearchChat.tsx`. Custom streaming: server emits a `data-research` UI-message part carrying `ResearchUIState` (`lib/research-state.ts`), read via `lib/read-research-stream.ts`. Uses `useChat` from `@ai-sdk/react` + `DefaultChatTransport`. Tailwind w/ Material-ish design tokens. Exercises target a local clone of this repo.
- Notable: he already streams *labeled steps* + progressive structured output — more advanced than the Lesson 0001 baseline.

## Lesson 7 note
- Schema/prompt nudging for `[n]` markers was unreliable. Learner shipped **deterministic post-processing** instead (`lib/citations.ts` → `prepareCitedText`): maps domains, markdown links, and numeric markers onto the numbered source list. Prefer this pattern when model discipline is the weak link.

## Open threads
- Exercises land in the real research-assistant codebase (local clone).
- Decide whether he wants AI Elements (Vercel's prebuilt AI components) or hand-rolled components for the retrofit.

## Phase 2 text arc (lessons 0001–0009) — closed
- Shipped: lifecycle, trust, HITL, perceived latency on the research assistant.
- Lesson 0009 audit completed; portfolio artifact (`docs/UX-RETROFIT.md`) skipped by choice.
- Motivation: personal AI apps + open source contribution, not job hunting. Skip interview/demo-script framing.

## Phase 2 voice & realtime arc (lesson 0010+)
- Primary tool: OpenAI Realtime API (WebRTC in browser).
- Lesson 0010 shipped: `/voice` probe with phase reducer, connection error mapping, `output_audio_buffer` handling for speaking→idle.
- Audio hygiene that fixed choppy responses: client `echoCancellation` + `noiseSuppression` + `autoGainControl`; server `noise_reduction: { type: 'far_field' }`. Default for future voice builds.
- Lesson 0011 shipped: partial transcripts — user confirmation after VAD commit, assistant stream during speaking.
- Lesson 0012 shipped: barge-in UX — interrupted turn flag, explicit `response.cancel` button, preserve/mark pattern from text stopped. Phase reducer needed a fix for explicit interrupt (likely `output_audio_buffer.cleared` / `response_cancel_not_active`).
- Lesson 0013: latency budget + VAD tuning — turn-latency readout (speech_stopped → first audio), tune `silence_duration_ms` against ~500–800 ms budget.

## Future topics (backlog)
- **Multimodal I/O** — vision input, image and audio output.
- **Voice in main app** — wire probe patterns into research assistant (lesson 0014 candidate).
- **semantic_vad** — when fixed silence fails on reflective speech.
