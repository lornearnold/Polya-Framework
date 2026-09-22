# polya_heuristic

A structured framework for an AI tutor, adapted from G. Polya's *How to Solve It* (1945). The goal is a tutor that helps a student work through a problem without taking the work away from them, and that builds the student's capacity to solve future problems independently.

[**View the slides**](https://lornearnold.github.io/polya_heuristic/presentation/slides.html) (also reachable from the [docs landing page](https://lornearnold.github.io/polya_heuristic/)).

## The framework

Problem solving moves through four sequential phases:

1. **Understand the problem.** Identify the unknown, the data, and the condition that ties them together.
2. **Make a plan.** Find a connection between the data and the unknown, drawing on related problems and prior results.
3. **Carry out the plan.** Execute each step and check it.
4. **Look back.** Examine the solution, the reasoning, and what is reusable in future problems.

Phases are navigated by dialogue. The tutor asks questions of the student, judges from the responses whether they are ready to advance, and chooses the next question accordingly. The questions are soft imperatives ("Could you restate the problem?"), not commands, and they should be questions the student could plausibly have asked themselves.

`framework/` holds the heuristic itself: the four phases, the question lists for each phase, and the supporting concepts (kinds of struggle, signs of progress, assessing readiness, trust). The whole thing is around 10K tokens and is loaded into the tutor's system prompt as one piece. Cross-references between files matter, so it is not chunked for retrieval.

## How the AI tutor uses it

The tutor is a single agent driven by a system prompt that includes the full framework plus three explicit instructions:

1. **Dual goal, ranked.** Help solve the problem and build capacity. Capacity is the more important of the two, and the prompt says so plainly. This is the anchor when the student asks for the answer.
2. **Reason from evidence.** The AI cannot empathize through shared experience. It infers the student's state from what the student has written and updates a model of their understanding as the dialogue proceeds.
3. **Improvise within the framework.** The question lists are reference, not a script. Rephrasing, specializing to the subject, bridging two questions, and inventing variants in the same spirit are all expected.

Few-shot examples in the prompt show the tutor redirecting "just give me the answer" requests back into the framework. This is the failure mode the framework most needs to defend against, and concrete examples constrain it more reliably than principles.

Readiness to advance between phases is a qualitative judgment, made in plain English at the transition points. It is not a numeric score and not a running tally.

## Student profile

The tutor maintains a representation of the student covering knowledge, skills, and history, recorded as dated observations rather than labels. Logged-in students get persistent profiles, updated after each session by an asynchronous background pass. Anonymous students get a default profile and a transient session profile that is not persisted. See `docs/student_profile.md`.

## Adapting the framework to a course

The framework is general. Each course produces three artifacts on top of it:

1. **Question relevance map.** Which framework questions matter most for this subject.
2. **Prerequisite knowledge map.** What the student is assumed to know coming in, so the tutor can tell productive struggle from unproductive struggle.
3. **Phase-mastery descriptions.** What "ready to advance" looks like for each phase in this course.

The recommended path is to provide the framework, the course objectives, and ten to twenty representative problems with annotated tutoring transcripts. The transcripts double as few-shot examples in the system prompt. See `docs/course_implementation.md`.

## Repository layout

- `framework/` — the heuristic, loaded whole into the tutor's system prompt.
- `docs/` — translation notes (1945 framework to 2026 AI), agent architecture, student profile, course implementation, the reveal.js presentation under `docs/presentation/`, and material preserved for implementers who want to formalize further. Served via GitHub Pages.
- `reference/` — personal archive, out of scope for tasks.

The framework is what stays the same across deployments. The course artifacts and the student profile are what changes.
