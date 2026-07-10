# Mode-switch state loss is now guarded

Lesson 0014 is done: Research and Voice share product chrome, and switching modes after work has begun requires confirmation because route navigation destroys the page-local conversation state. The learner recognized state loss as a product decision that needs explicit user consent, not an implementation detail to hide.

**Implications:** The destructive boundary is now legible. Next, preserve the one piece of state that should cross it: carry a voice conversation into Research as an editable draft while still ending the Realtime session.
