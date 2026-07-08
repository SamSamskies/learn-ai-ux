# Trust bar shipped in the research assistant

The learner implemented `generateConfidenceCopy`, a scan-height `TrustBar` with calibrated uncertainty, provenance chips, source count (with anchor to `#brief-sources`), and explicit "No sources cited" empty state. Wired into `BriefArticle` after the headline; removed the footer confidence dump.

**Evidence:** user reported lesson 5 complete; code review confirms `lib/generate-confidence-copy.ts`, `components/ResearchChat/TrustBar.tsx`, and `BriefArticle` placement match the lesson spec.

**Implications:** trust-signal arc is in place at scan height. Next arc is **human-in-the-loop** — `New Chat` is a one-click destructive action (clears conversation, server session, uploaded docs) with no confirmation gate.
