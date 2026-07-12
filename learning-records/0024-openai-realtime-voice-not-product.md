# OpenAI Realtime voice is not a product surface (for this mission)

Learner wrap-up after lessons 0010–0020: Realtime speech-to-speech feels useless in practice — unreliable STT (LR-0022), no win from semantic VAD (LR-0018), and multimodal output that isn't worth shipping (LR-0023). The arc taught transferable UX; the model/stack did not clear the bar for personal apps.

**Implications:** Voice arc closed. Do not push more Realtime polish as the default next step. Keep Research (text) as the product surface. Patterns that still matter elsewhere: phase lifecycle, barge-in / preserve-interrupted, latency budgets, mode switch with state-loss guards, handoff with edit-before-send, split-by-risk tool approval. Revisit voice only if a different provider/stack or a clear personal use case appears.
