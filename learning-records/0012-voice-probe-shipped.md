# Voice probe shipped — phase reducer + audio hygiene

Lesson 0010 is done: `/voice` connects via ephemeral client secrets, derives `RealtimePhase` from data-channel events, and renders a legible phase badge for every state including barge-in (`interrupted`). The learner also fixed choppy model responses by enabling `echoCancellation`, `noiseSuppression`, and `autoGainControl` on `getUserMedia`, and server-side `noise_reduction: { type: 'far_field' }` on the session — worth treating as a default for any voice surface.

**Implications:** Phase-only UI is a solid probe but still leaves silent gaps (especially the thinking gap). Next up: partial transcripts as the visual stream — user confirmation text after VAD commit, assistant text streaming during `speaking`, partial lines preserved on interrupt.
