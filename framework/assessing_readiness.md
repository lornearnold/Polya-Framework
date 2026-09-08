# Assessing readiness

The teacher continually judges whether the student is ready to move on from the current phase. This judgment is not a property of the student; it is the teacher's read on a hidden cognitive state, used to decide when to advance, when to keep dialoguing, and when to course-correct.

The judgment is qualitative and graded. The teacher should think of it as a position on a spectrum from "not confident" through "tentatively confident" to "confident," where the cut points depend on the topic, the stage of the course, and what the teacher knows about the student. The bar for advancing is the point on that spectrum past which less value stands to be gained by continuing within the current phase than by proceeding to the next.

## Phases the teacher assesses

- Readiness to plan, after Phase 1 (understanding)
- Readiness to execute, after Phase 2 (planning)
- Readiness to finish, after Phase 4 (reflection)

Phase 3 (execution) does not require this kind of readiness judgment. The teacher tracks step completion in execution rather than readiness; see [3_execute.md](3_execute.md).

## When to make the judgment explicit

The judgment is most useful at decision points, especially **phase transitions**: deciding to move from understanding to planning, from planning to execution, from execution to reflection. Within a phase, the teacher is mostly choosing the next question, not re-evaluating readiness. At phase transitions, the teacher should make the reasoning explicit: what evidence supports advancing, what evidence argues against, and what the student would have to demonstrate for the case to flip.

## Shifts in readiness

A shift in the teacher's read of readiness, from one dialogue step to the next, is itself a plausible reading rather than a measurement. A move that looks like progress is a sign that progress was made, not a confirmation. The teacher should commit to the reading tentatively and remain ready to revise. See [signs_of_progress.md](signs_of_progress.md) for the observable signals that justify shifts in readiness.

## How an AI tutor should reason about readiness

The AI should:

- Reason about readiness in plain English at decision points ("the student has restated the problem in their own words, named the unknown, and given a sensible expected outcome; that is enough to advance to planning").
- Use qualitative notes for between-session memory ("solid grasp of Phase 1 questions for problems involving rates of change"). See [student_profile.md](../docs/student_profile.md).

The AI should not:

- Produce a numerical estimate of readiness. The judgment is qualitative.
- Treat the bar for advancing as a hard threshold. It is a soft consideration in a judgment.
- Try to maintain a running readiness score across turns. Reason about readiness at decision points; do not track a tally.

A more formal treatment of readiness using probabilistic notation, including a Bayesian framing, is preserved in [future_considerations.md](../docs/future_considerations.md) for implementers who want one.
