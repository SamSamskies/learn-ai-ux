# Mission: AI Product UX & Interaction Design (Roadmap Phase 2)

## Why
I'm a 10+ year frontend engineer leveling up as an AI Product Engineer — not for a job hunt, but to build good AI apps for myself and contribute useful UX patterns to open source. My edge over backend/ML engineers is interfaces, and the hardest part of an AI product is the UX over nondeterministic, streaming, sometimes-wrong output.

## Success looks like
- I have **retrofitted polished AI UX onto my Phase 1 research assistant** (Vercel AI SDK + Next.js/React) so it feels like a real product, not a demo.
- I can design and implement the full **response lifecycle**: idle, submitted, thinking, streaming, complete, stopped, and error — each with a deliberate UI treatment.
- I can build **human-in-the-loop** flows (tool/action approval, edit-before-send, confirm destructive actions).
- I can surface **trust signals**: citations, sources, and calibrated uncertainty rather than false confidence.
- I can reason about **perceived latency** (acknowledge instantly, make progress legible, know when to add strategic friction) and apply optimistic updates.
- I can explain the UX decisions behind my builds — in code comments, PRs, or docs — so others can learn from or reuse them.

## Next horizon (planned, after the text-surface core)
Text is only one surface. Voice and multimodal are one of the fastest-growing product areas, and the UX of a nondeterministic *voice* agent plays directly to my frontend background — it's exactly the kind of hard interface problem I want to own. Once the text-surface retrofit is solid, extend into:
- **Speech-to-speech and realtime interaction** — low-latency voice agents.
- **Interruption / barge-in and turn-taking** — letting the user talk over the agent and handing control back cleanly.
- **Partial transcripts and live "thinking" cues** — both audio and visual.
- **Multimodal I/O** — vision input, image and audio output.
- **Latency budgets for realtime** — where "fast enough" is a hard requirement, not a nicety.

Primary tool: OpenAI Realtime API (speech-to-speech, low-latency voice agents).

## Constraints
- **Time:** ~20 min per lesson — one tangible win per session.
- **Format:** short concept explainer, then a hands-on build/exercise in a real repo. Build-heavy.
- **Stack:** Vercel AI SDK + Next.js/React (matches Phase 1 AI SDK work).
- Solo, self-directed, evenings/weekends cadence.

## Out of scope (for now)
- Backend/model internals, RAG, agents, evals as primary topics (later roadmap phases). Touch only where they change the UX.
- Native mobile UI. Web first.
- Visual/brand design systems from scratch — reuse existing UI, focus on interaction over nondeterministic output.
