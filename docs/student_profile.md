# Student profile

The AI tutor's representation of the student. Used to choose the right next question, to distinguish productive from unproductive struggle, and to start a session at the right place. See [getting_to_know_the_student.md](../framework/getting_to_know_the_student.md) for the underlying concept; this file specifies what the AI tracks and how.

## Categories

1. **Knowledge state.** Concepts the student has demonstrated mastery of. Drives the depth of questions in the understanding stage.
2. **Skill state.** Operations and problem-solving steps the student has demonstrated mastery of. Drives the depth of questions in the planning stage.
3. **History.** Problems worked, outcomes, particularly memorable methods or results that may be reusable.

## Form

Structured fields for knowledge state and skill state, so they can be queried directly. Free-form notes for history. Updates happen at the end of each session by the asynchronous student-model updater (see [agent_architecture.md](agent_architecture.md)). The student should be able to inspect their profile.

## What not to record

- Permanent labels that can become self-fulfilling ("weak in X"). Prefer dated observations: "as of 2026-04, asks for hints before trying Section 4 questions."
- Personal data unrelated to learning.
- Full transcripts. Use summaries, with pointers if raw transcripts are retained elsewhere.

## Default profile

The default profile assumes the student has basic knowledge of the course prerequisites and basic skill in the problem-solving operations. Knowledge and skill entries are recorded only when a student demonstrates more than basic knowledge or skill in course-specific areas; otherwise the default applies, even for known students.

## Anonymous sessions

For students who are not logged in, the profile is the default profile. The session may still build a transient profile within its own context, but nothing is persisted.
