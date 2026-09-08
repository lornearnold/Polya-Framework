# Student profile

The AI tutor's representation of the student. Used to choose the right next question, to distinguish productive from unproductive struggle, and to start a session at the right place. See [getting_to_know_the_student.md](../framework/getting_to_know_the_student.md) for the underlying concept; this file specifies what the AI tracks and how.

## Categories

1. **Knowledge state.** Concepts the student has demonstrated mastery of; recurring gaps. Drives whether an obstacle is productive or unproductive struggle.
2. **Skill state.** Which problem-solving operations the student performs spontaneously and which require prompting. Drives where in the question hierarchy to begin.
3. **Disposition.** What the student tends to skip, how long their tolerance for productive struggle runs, whether reflection is welcomed or resisted.
4. **History.** Problems worked, outcomes, particularly memorable methods or results that may be reusable.
5. **Communication style.** Brief vs. detailed, formal vs. informal, visual vs. verbal. Affects question form, not question selection.

## Form

Structured fields for knowledge state and skill state, so they can be queried directly. Free-form notes for the other three categories. Updates happen at the end of each session by the asynchronous student-model updater (see [agent_architecture.md](agent_architecture.md)). The student should be able to inspect their profile.

## What not to record

- Permanent labels that can become self-fulfilling ("weak in X"). Prefer dated observations: "as of 2026-04, asks for hints before trying Section 4 questions."
- Personal data unrelated to learning.
- Full transcripts. Use summaries, with pointers if raw transcripts are retained elsewhere.

## Anonymous sessions

For students who are not logged in, the profile is the default profile from [translation_notes.md](translation_notes.md). The session may still build a transient profile within its own context, but nothing is persisted.
