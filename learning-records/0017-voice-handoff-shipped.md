# Voice → Research handoff preserves intent across a lossy boundary

Lesson 0015 is done: "Continue in Research" ends the Realtime session but carries the last six transcript turns (plus a pending user utterance) into the Research composer via a one-shot `sessionStorage` buffer. The user reviews and edits before send — same edit-before-send HITL contract as text.

**Implications:** Mode-switch UX is now complete for v1 (guard destructive exits + carry intent). The voice arc can move to turn-boundary quality: when fixed `silence_duration_ms` fails on reflective speech, switch to `semantic_vad`.
