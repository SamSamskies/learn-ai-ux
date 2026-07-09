# Barge-in UX shipped — interrupted turns + explicit cancel

Lesson 0012 is done: interrupted assistant turns carry an `interrupted: true` flag in the transcript reducer, render with a muted Interrupted badge, and the probe exposes an Interrupt button that sends `response.cancel` while `speaking`. The learner hit a phase-reducer bug on explicit interrupt (phase stuck or wrong transition) and fixed it by extending `reduceRealtimePhase` — likely handling `output_audio_buffer.cleared` and/or `response_cancel_not_active` so the explicit path matches VAD barge-in.

**Implications:** Turn-taking UX is legible on both interrupt paths. Next up: measure and tune the latency stack — VAD tail + thinking gap against the ~500–800 ms conversational budget, using the probe as a tuning surface.
