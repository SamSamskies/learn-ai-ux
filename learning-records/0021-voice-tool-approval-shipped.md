# Voice tool approval shipped — gate side effects, keep lookups auto-run

Lesson 0019 shipped: `stage_research_brief` holds on `function_call` until ConfirmDialog approval; `lookup_definition` stays auto-run. Approve writes the Research handoff; reject still sends `function_call_output` + `response.create` so speech continues.

**Implications:** Split-by-risk tool UX is established on voice. Next: multimodal *output* — generate an image via a Realtime tool, but confirm/edit the prompt on screen first (STT is unreliable for creative prompts).
