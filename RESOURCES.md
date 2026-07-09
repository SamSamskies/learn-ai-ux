# AI Product UX & Interaction Design — Resources

## Knowledge

### Foundational patterns & principles
- [Shape of AI — shapeof.ai](https://www.shapeof.ai/)
  Open pattern library (Emily Campbell) organizing AI UX into six categories: Wayfinders, Prompt Actions, Tuners, Governors, Trust Builders, Identifiers. Use for: a shared vocabulary of patterns and as a diagnostic checklist when a feature has low adoption. ([overview](https://amirelion.com/blog/shape-of-ai-pattern-library-ai-ux-design))
- [arablex/llm-ux-patterns (GitHub)](https://github.com/arablex/llm-ux-patterns)
  Production-tested patterns shown on real screens, not mockups: streaming *steps* (not just tokens), RAG citations, token/cost transparency, quota/rate-limit fallback, eval ledgers, AI empty states. Use for: concrete "what does good look like" references when building.
- [NN/g — Designing AI Products and Features: Study Guide](https://www.nngroup.com/articles/designing-ai-study-guide/)
  Curated hub of Nielsen Norman research on AI UX. Use for: authoritative, research-grounded guidance and as a jumping-off point.

### Specific topics
- [NN/g — AI: First New UI Paradigm in 60 Years](https://www.nngroup.com/articles/ai-paradigm/)
  Frames generative AI as "intent-based outcome specification" — users say *what* they want, not *how*. Use for: the mental model behind why AI UX is different, and why hybrid (chat + GUI) interfaces win.
- [NN/g — Generative UI and Outcome-Oriented Design](https://www.nngroup.com/articles/generative-ui/)
  Distinguishes true genUI (real-time AI-generated interfaces) from AI-assisted design; argues designers become authors of *constraints/guardrails*. Use for: the generative/dynamic UI lessons.
- [NN/g — GenUI In Real Life: Buttons and Checkboxes](https://www.nngroup.com/articles/genui-buttons-and-checkboxes/)
  Real examples (Claude's AskUserQuestion, Google AI Mode checkboxes) of simple GUI widgets injected into chat to reduce friction. Use for: human-in-the-loop and hybrid-input lessons.
- [The Trust-Latency Gap — UX Collective](https://uxdesign.cc/the-trust-latency-gap-why-the-future-of-ux-is-intentionally-slower-3433c1787d5e)
  Argues that as AI execution nears zero latency, trust needs *strategic friction* — deliberate speed bumps that build confidence. Use for: perceived-latency and confirmation-flow lessons.
- [Shape of AI — Citations pattern](https://www.shapeof.ai/patterns/citations)
  Where to place citations, metadata for scanning, hover previews, and why missing sources must be explicit. Use for: trust-signal and citation lessons.
- [Shape of AI — Verification pattern](https://www.shapeof.ai/patterns/verification)
  When to require human verification before AI actions, matching friction to harm/scope/reversibility. Use for: human-in-the-loop and destructive-action confirmation lessons.
- [Shape of AI — Prompt enhancer pattern](https://www.shapeof.ai/patterns/prompt-enhancer)
  Explicit, reviewable prompt rewriting before a run — preserve intent, never auto-send, offer undo. Use for: edit-before-send and composer-assistance lessons.

### Implementation (stack)
- [Vercel AI SDK — Chatbot (useChat)](https://ai-sdk.dev/docs/ai-sdk-ui/chatbot)
  Canonical docs for `useChat`: message streaming, managed `status` (`submitted | streaming | ready | error`), `error`, `stop`, throttling UI updates. Use for: every hands-on build in this phase.
- [Vercel AI SDK — Troubleshooting: Streaming Status Shows But No Text Appears](https://ai-sdk.dev/docs/troubleshooting/streaming-status-delay)
  Explains the "streaming but empty" gap: status flips to `streaming` on connection (incl. metadata) before tokens arrive. Use for: correctly distinguishing "thinking" from "typing" in the UI.
- [vercel/ai — chat.ts source (ChatStatus)](https://github.com/vercel/ai/blob/main/packages/ai/src/ui/chat.ts)
  The source of truth for the status state machine and abort handling. Use for: when docs are ambiguous about edge cases (abort, network errors).

### Voice, realtime & multimodal (Phase 2)
- [OpenAI — Voice agents](https://developers.openai.com/api/docs/guides/voice-agents)
  Architecture choice: speech-to-speech (Realtime API) vs chained STT→agent→TTS. Browser path uses ephemeral client secrets + WebRTC. Use for: lesson 0010+ hands-on builds.
- [OpenAI Realtime API — docs](https://platform.openai.com/docs/guides/realtime)
  Speech-to-speech, low-latency voice agents over WebRTC/WebSocket. Handles audio in/out, interruption/barge-in, and turn detection server-side. Use for: the realtime interaction, barge-in/turn-taking, and latency-budget lessons.
- [OpenAI — Realtime API with WebRTC](https://developers.openai.com/api/docs/guides/realtime-webrtc)
  Ephemeral token mint + browser peer connection flow. Use for: implementing the voice probe and connection-phase UI.
- [openai/openai-realtime-console (GitHub)](https://github.com/openai/openai-realtime-console/)
  Lightweight reference app for WebRTC Realtime. Use for: comparing event handling when your probe behaves unexpectedly.
- [OpenAI — Realtime transcription](https://developers.openai.com/api/docs/guides/realtime-transcription)
  Input vs output transcript events, VAD commit timing, `audio.input.transcription` session config. Use for: lesson 0011 partial-transcript builds.
- [OpenAI — Realtime conversations (interruption & truncation)](https://developers.openai.com/api/docs/guides/realtime-conversations#interruption-and-truncation)
  VAD barge-in, `response.cancel` / `response.cancelled`, WebRTC auto-truncation vs WebSocket `conversation.item.truncate`. Use for: lesson 0012 barge-in UX.
- [OpenAI — Realtime VAD (voice activity detection)](https://developers.openai.com/api/docs/guides/realtime-vad)
  `server_vad` vs `semantic_vad`, `silence_duration_ms`, `threshold`, `prefix_padding_ms`, `interrupt_response`. Use for: lesson 0013 latency budget & VAD tuning.

## Wisdom (Communities)
- [r/UXDesign](https://reddit.com/r/UXDesign) and [r/UI_Design](https://reddit.com/r/UI_Design)
  Use for: critique of interaction patterns and before/after retrofits.
- [Vercel AI SDK GitHub Discussions/Issues](https://github.com/vercel/ai/discussions)
  Use for: implementation edge cases (streaming, status, aborts) with maintainer responses.
- **TODO:** find a higher-signal, AI-UX-specific community (Discord/Slack). Current UX subreddits are broad.

## Gaps
- No single authoritative text on *implementing* AI UX patterns end-to-end — knowledge is scattered across the pattern libraries + framework docs. Lessons will stitch these together.
- Need a trusted source specifically on **optimistic updates / perceived-performance** for AI (beyond the trust-latency essay).
