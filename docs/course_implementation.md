# Course-specific implementation

The framework is general. Adopting it for a course requires concrete decisions about content, problems, and what mastery looks like. This file describes the recommended approach and the deliverables that approach produces.

## Approaches, ordered by cost

1. **Full hand-curation.** The instructor provides content, objectives, an exhaustive problem list, and example questions per problem. Highest fidelity, highest cost. Best for a small set of high-stakes problems.
2. **Hand content, AI mapping.** The instructor provides content, objectives, and sample problems; the AI maps the framework onto the course. Lower cost; fidelity depends on the AI's grasp of the subject.
3. **Curated examples plus AI generation.** The instructor provides framework, objectives, and ten to twenty representative problems with annotated tutoring transcripts. The AI generalizes to new problems by analogy. Compact way to encode the instructor's intent.
4. **Iterative refinement of approach 2.** The AI does the initial mapping, the instructor reviews and corrects, and results feed back into prompts and examples.
5. **AI-assisted course design.** The AI helps the instructor structure objectives and identify learning operations from existing course materials.

## Recommended approach

Approach 3 (curated examples plus AI generation) is the practical sweet spot. Annotated transcripts encode tacit instructor judgment more compactly than exhaustive lists, and they serve double duty as few-shot examples in the system prompt described in [translation_notes.md](translation_notes.md).

## Deliverables

Regardless of approach, three concrete deliverables come out of the mapping work for each course:

1. **Question relevance map.** Which framework questions are most often useful for the course's problem types, and which are rarely needed.
2. **Prerequisite knowledge map.** What the student is assumed to know before the course begins, so the tutor can distinguish productive from unproductive struggle. See [kinds_of_struggle.md](../framework/kinds_of_struggle.md).
3. **Phase-mastery descriptions.** What "ready enough to advance" looks like for each phase in this course, so the readiness judgment has concrete content rather than vague approval. See [assessing_readiness.md](../framework/assessing_readiness.md).

The framework is what stays the same across courses. These three deliverables are what changes.
