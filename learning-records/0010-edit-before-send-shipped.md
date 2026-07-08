# Edit-before-send shipped on the composer

The learner wired explicit prompt refinement on the research assistant composer: a lightweight `/api/refine-prompt` endpoint, Refine button with undo, a "Refined — review before sending" banner, and guardrails (no auto-send, disabled while busy/uploading, minimum draft length). Human-in-the-loop now spans session reset (L6), claim verification (L7), and pre-run intent shaping (L8).

**Evidence:** user reported lesson 8 complete; code review confirms `lib/refine-prompt.ts`, `app/api/refine-prompt/route.ts`, refine/undo state in `ResearchChat/index.tsx`, and Refine UI in `ChatComposer.tsx`.

**Implications:** the text-surface retrofit arc is ready to close with a wrap-up lesson — audit checklist, before/after narrative, and portfolio-ready decision log. Next horizon: voice/realtime (OpenAI Realtime API).
