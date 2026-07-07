# learn-ai-ux

**Phase 2 of my [AI Product Engineer roadmap](https://github.com/SamSamskies/ai-product-engineer-roadmap): AI Product UX & Interaction Design.**

This is a stateful *teaching workspace*, not an app. It's where I go deep on making nondeterministic, streaming AI feel fast, trustworthy, and usable — turning a 10+ year frontend background into a differentiator. Sibling repos: [`learncursor`](https://github.com/SamSamskies/learncursor) (Phase 0) and [`learnopenai`](https://github.com/SamSamskies/learnopenai) (Phase 1).

## The mission

Retrofit polished AI UX onto my Phase 1 [research assistant](https://github.com/SamSamskies/learnopenai/tree/main/research-assistant) (Vercel AI SDK + Next.js/React), learned through short-explainer-then-build lessons (~20 min each). Full details in [`MISSION.md`](./MISSION.md).

## How this workspace is organized

| Path | What it is |
| --- | --- |
| [`MISSION.md`](./MISSION.md) | The *why* — the concrete goal every lesson traces back to. |
| [`RESOURCES.md`](./RESOURCES.md) | Curated, high-trust sources (knowledge) and communities (wisdom). |
| [`GLOSSARY.md`](./GLOSSARY.md) | The canonical vocabulary for the topic. |
| [`NOTES.md`](./NOTES.md) | Working notes and learner preferences. |
| [`lessons/`](./lessons) | Self-contained HTML lessons — the primary unit of teaching. Open in a browser. |
| [`reference/`](./reference) | Compressed cheat sheets, revisited long after a lesson is done. |
| [`assets/`](./assets) | Shared components (e.g. `course.css`) so every lesson reads as one book. |
| [`learning-records/`](./learning-records) | ADR-style records of what's been learned and why — they steer what's taught next. |

Lessons and references are static HTML — no build step. Open them directly:

```bash
open lessons/0001-response-lifecycle.html
```

## Progress

**Lessons**

1. [The Response Lifecycle](./lessons/0001-response-lifecycle.html) — designing every state of a nondeterministic reply (idle → submitted → thinking → streaming → complete, plus stopped/error exits).
2. [Designing the Interrupted State](./lessons/0002-interrupted-state.html) — preserve / mark / recover when the user hits Stop; retry-in-place with `regenerate({ messageId })`.

**Reference**

- [The Response Lifecycle](./reference/response-lifecycle.html) — state-by-state cheat sheet with AI SDK signals.

## The teaching method

Each lesson is short and tied to the mission, sits in my zone of proximal development, cites a high-trust primary source, and pairs a tight concept explainer with a hands-on build in the real research-assistant repo. Knowledge comes from trusted resources; skills come from effortful, feedback-driven practice. Powered by a `teach` agent skill.

## Related

- [AI Product Engineer roadmap](https://github.com/SamSamskies/ai-product-engineer-roadmap) — the overall plan (Phases 0–11).
- [research-assistant](https://github.com/SamSamskies/learnopenai/tree/main/research-assistant) — the Phase 1 project being retrofitted throughout this phase.
