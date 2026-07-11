# Semantic VAD didn't beat tuned server_vad for this voice surface

Lesson 0016 shipped: centralized turn-detection config, semantic_vad with low eagerness, and a legible mode label. Smoke tests showed no meaningful improvement over server_vad at 500 ms — if anything, server_vad felt snappier and more predictable. Mid-thought cutoffs weren't a real pain point for this learner's speech pattern and use case.

**Implications:** Default back to `server_vad` + defended `silence_duration_ms: 500` for the research-assistant voice mode. Keep the centralized config and UI label — they're still valuable when VAD mode changes. Reserve semantic_vad for surfaces where measured cutoffs actually fail (reflective monologues, heavy filler). Don't teach VAD mode comparison again unless symptoms reappear.
