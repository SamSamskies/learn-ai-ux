# Partial transcripts shipped — turn log on /voice

Lesson 0011 is done: the voice probe splits phase and transcript into separate reducers, enables input transcription at session mint, and renders a scrollable turn log with user confirmation text (post-VAD) and streaming assistant drafts. Partial assistant lines survive `response.cancelled` — the preserve rule from text `stopped` already works at the data layer.

**Implications:** The probe now shows *what* is happening, not just *where* in the lifecycle. Next up: make barge-in legible in the UI — mark interrupted turns distinctly, add an explicit interrupt control, and wire `response.cancel` so users can stop the model without talking over it.
