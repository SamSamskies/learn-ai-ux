# Destructive-action confirm dialog shipped

The learner implemented a reusable `ConfirmDialog` and gated `New Chat` with risk-aware friction: instant reset when the chat is empty with no uploads, modal with explicit consequence copy otherwise. Cancel gets focus; Escape and backdrop dismiss without side effects.

**Evidence:** user reported lesson 6 complete; code review confirms `components/ConfirmDialog.tsx` and gated `newChat` flow in `ResearchChat/index.tsx` match the lesson spec.

**Implications:** human-in-the-loop arc started with session reset. Trust signals still lack **claim-level** linkage — sources live at the bottom but key points don't cite them. Next: inline citation markers on key points, numbered source list with bidirectional anchors.
