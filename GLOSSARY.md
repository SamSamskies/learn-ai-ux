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

**Transport error**:
A failure in the HTTP/stream layer (network, auth, 5xx, SDK parse) before or during delivery — distinct from a domain error streamed inside app state. Surfaces via `useChat`'s top-level `error`; must be mapped to plain-language copy client-side.
_Avoid_: fetch error, API error

**Friendly error mapping**:
Translating raw SDK or HTTP error text into specific, blame-free, actionable product copy — never showing `error.message` directly to users.
_Avoid_: error handling, error messages

**Trust signal**:
A UI element that helps users judge whether to believe an AI output and how hard to verify it — provenance chips, source links, calibrated confidence.
_Avoid_: trust badge, credibility indicator

**Calibrated uncertainty**:
Surfacing model confidence as honest, actionable copy ("verify key claims") rather than raw enum values or false precision.
_Avoid_: confidence score, certainty level
