# Agent architecture

Notes on when a multi-agent setup is justified for the AI tutor.

## Default: single-agent

Start single-agent. A strong system prompt with the dual goal, the framework as context, and few-shot examples (see [translation_notes.md](translation_notes.md)) handles most of the tutor's job. Per-turn agent layers add latency and complexity that damage the conversational feel of tutoring, which has its own learning value.

## Justified additions

Two roles earn their cost in observable ways and should be added when the corresponding need is observed in deployment:

### Student-model updater (asynchronous)

Reads each completed session transcript and updates the student profile (see [student_profile.md](student_profile.md)). Runs after the session, not in the loop. Keeps profile maintenance out of the tutor's context window and makes profile updates auditable.

### Protocol-conformance reviewer (sampled)

Periodically reviews a sample of tutor transcripts and flags off-protocol behavior: gave away answers, skipped reflection, mismatched the student's level. Drives prompt and content refinement, not real-time correction. Worthwhile at scale.

## Not justified

A per-turn critic agent that gates every tutor reply is not recommended. The same effect is reachable with a stronger system prompt and few-shot examples, and the latency cost is paid every turn rather than amortized.
