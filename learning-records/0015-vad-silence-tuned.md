# VAD silence tuned to 500 ms — snappy Q&A feels right

Lesson 0013 is done: turn-latency readout is live on the probe, and dropping `silence_duration_ms` from 700 → 500 feels nicer for conversational back-and-forth. The learner validated the product knob with measurement, not vibes — VAD tail is now a defended choice against the ~500–800 ms budget.

**Implications:** Probe UX stack (lifecycle, transcripts, barge-in, latency) is product-ready. Next: wire voice into the research assistant as a first-class mode — don't merge Realtime into the text research pipeline; mode-switch with shared chrome and voice-appropriate instructions.
