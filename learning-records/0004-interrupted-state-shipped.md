# Interrupted state shipped in the research assistant

The learner implemented `StoppedNotice` with preserve / mark / recover, `interrupted` detection in the turn loop, `regenerate({ messageId })` for stopped and domain-error retries, and `canRegenerate={isLast}` for the edge case where only the latest turn can be retried. The response lifecycle is now complete except for one gap: the bottom transport `ErrorBanner` still renders raw `error.message` and retries via `retryQuestion` (duplicate turn).

**Evidence:** user reported lesson 2 complete; code review of `ResearchChat/index.tsx` confirms `StoppedNotice`, `interrupted`, and domain-error `regenerate` are in place. Transport error path at lines ~479–487 is unchanged.

**Implications:** teach friendly transport-error mapping next (LR-0003 gap #3). After that, lifecycle retrofit is done — move to perceived latency / human-in-the-loop / trust signals.
