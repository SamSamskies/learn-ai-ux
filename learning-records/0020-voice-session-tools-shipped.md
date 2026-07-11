# Voice session tools shipped — legible lookup loop

Lesson 0018 shipped: `lookup_definition` registered on the Realtime session, client-side detect on `response.done`, stub lookup API, "Looking up…" dock label, and transcript system line on completion. Read-only tools auto-run with a visible pause label.

**Implications:** The Realtime tool loop (detect → execute → `function_call_output` → `response.create`) is a known pattern. Next: gate side-effecting tools with approval before execution — reuse the text-surface HITL risk model (lookup = low, stage/navigate = medium). Don't register heavy research search on voice.
