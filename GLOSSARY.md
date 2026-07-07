# AI Product UX Glossary

The canonical language for this workspace. All lessons, exercises, and records use these terms. Terms are added only once demonstrated understood — this is a record of compressed knowledge, not a dictionary to read cold.

## Terms

**Response lifecycle**:
The ordered set of states an AI reply moves through — idle → submitted → thinking → streaming → complete, with stopped and error as exits. Each state needs a deliberate UI treatment.
_Avoid_: loading state, request/response

**Thinking gap**:
The interval after a request is sent but before the first token renders. In the AI SDK, `status` is already `streaming` here (connection open, metadata flowing) but no text has arrived — so it must be detected by checking for empty message parts, not by status alone.
_Avoid_: loading, spinner time

**Perceived latency**:
How slow an interaction *feels*, as opposed to how slow it *is*. Governed by instant acknowledgement and legible progress, not just raw speed.
_Avoid_: performance, actual latency

**Strategic friction**:
Deliberately slowing or gating an interaction (a confirmation, a review step) to build trust or prevent harm, used where speed would erode confidence.
_Avoid_: speed bump, delay

**Interrupted state (stopped)**:
The lifecycle exit where the user aborts a reply mid-stream. Designed with three rules: preserve partial output, mark it as user-stopped (not an error), and offer a clear recovery (regenerate in place).
_Avoid_: cancelled, aborted, failed

**Regenerate in place**:
Retrying a specific turn via `regenerate({ messageId })` so the SDK drops messages after it and replaces that answer — as opposed to re-sending the question text, which appends a duplicate turn.
_Avoid_: retry, resend
