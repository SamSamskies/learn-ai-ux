# Inline citations shipped via post-processing

The learner wired claim-level citation markers on key points with a numbered source list and bidirectional anchors. Instead of relying on schema descriptions and system-prompt nudging alone, they built deterministic post-processing in `lib/citations.ts` (`prepareCitedText`) — mapping model-emitted domains, markdown links, and numeric markers onto the numbered source list. Citations are looking good in practice.

**Evidence:** user reported lesson 7 complete; noted prompt/schema nudging was unreliable and they took the post-processing approach; code review confirms `prepareCitedText`, `BriefArticle` citation components, and numbered `#brief-sources` anchors.

**Implications:** trust arc is complete at both scan height (TrustBar) and claim level (inline markers). Human-in-the-loop arc continues with **edit-before-send** on the composer — review a refined draft before triggering an expensive research run. After that, a retrofit wrap-up closes the text-surface mission.
