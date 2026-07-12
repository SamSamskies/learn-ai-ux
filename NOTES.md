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

## Phase 2 voice & realtime arc (lessons 0010–0021) — closed
- Primary tool tried: OpenAI Realtime API (WebRTC in browser).
- Lesson 0010: `/voice` probe with phase reducer, connection error mapping, `output_audio_buffer` for speaking→idle.
- Audio hygiene: client `echoCancellation` + `noiseSuppression` + `autoGainControl`; server `noise_reduction: { type: 'far_field' }`.
- Lesson 0011: partial transcripts — user confirmation after VAD commit, assistant stream during speaking.
- Lesson 0012: barge-in UX — interrupted turn flag, explicit `response.cancel`, preserve/mark pattern.
- Lesson 0013: turn-latency readout; `silence_duration_ms: 500` for snappy Q&A.
- Lesson 0014: mode switch (Research | Voice), shared chrome; confirm before switch destroys route-local state. Do NOT merge Realtime into useChat.
- Lesson 0015: Voice → Research handoff — one-shot buffer seeds Research composer; tear down Realtime.
- Lesson 0016 / LR-0018: semantic VAD no win — default stays `server_vad` at 500 ms; keep centralized config.
- Lesson 0017: voice + image context (attach JPEG, thumbnail); handoff text-only v1.
- Lesson 0018: `lookup_definition` auto-run tool loop (LR-0020).
- Lesson 0019: gate `stage_research_brief`; lookup stays auto-run. LR-0022: STT unreliable — confirm/edit on screen.
- Lesson 0020 / LR-0023: voice image output gated + editable — results unusable; wouldn't ship.
- Lesson 0021 / LR-0024: wrap-up — **OpenAI Realtime voice is not a product surface**; Research text remains the product. Checklist: `reference/voice-arc-checklist.html`.

## Future topics (backlog)
- Deepen text Research (agents / tool HITL on text, personal workflows).
- Non-Realtime multimodal (if quality bar can be cleared without S2S).
- Ship something personal with Phase 2 text baseline; pause new arcs if preferred.
