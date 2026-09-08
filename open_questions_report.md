# Report: Responses to Open Questions

This report works through the questions in `open_questions.md`. Each section names the question, gives a short answer, and explains the reasoning. Where the answer points to a concrete change in the framework, that is called out.

---

## 1. Are the listed Polya concepts adequately represented in the framework?

The six entries reviewed are: *variation of the problem*, *signs of progress*, *progress and achievement*, *modern heuristic*, *bright idea*, *did you use all the data*. The framework captures most of the load-bearing ideas. A few specific things are missing or weak.

### Variation of the problem
Captured well in `questions_for_planning.md` (Section 4) and in the "two motions, repeated" passage of `planning.md`. Two ideas from Polya are not carried over:

- **Variation as a way to keep attention alive when stuck.** Polya stresses that varying the problem is not only a generative move but also a way to reconquer interest when the student is tiring. The framework treats varying the problem as a search strategy. It should also note that varying serves the student's stamina, not just their search. This connects to `kinds_of_struggle.md` and could be added there or in `planning.md`.
- **The named modes of variation.** Polya lists going back to the definition, decomposing and recombining, introducing auxiliary elements, generalization, specialization, and analogy as canonical modes. The framework includes generalization, specialization, and analogy in the planning questions but not the others. "Decomposing and recombining" and "going back to the definition" are useful enough that they should appear at least once in `questions_for_planning.md`, even briefly.

### Signs of progress
The framework captures this concept indirectly through `little_successes.md` and the $\Delta E(X)$ derived quantity in `confidence_that.md`. What is missing:

- **Signs of progress are plausible, not certain.** Polya's "trust but look" is the heuristic posture toward signs. The framework's $\Delta E(X) \geq 0$ check assumes a clean read on whether progress was made. In practice the teacher should commit to a direction tentatively and remain ready to revise. Adding a short note to `confidence_that.md` that $\Delta E(X)$ is itself a plausible reading rather than a measurement would tighten this.
- **The link between specific student moves and signs of progress.** Polya names concrete signs: bringing an unused datum into play, taking a previously ignored clause into account, an analogous problem coming to mind. These are exactly the events that should drive the teacher to update $E(X)$ upward. Making this connection explicit would help an AI tutor reason about what counts as evidence.

### Progress and achievement
Mostly captured. The conspicuous omission is the named pair **mobilization** (extracting relevant prior knowledge from memory) and **organization** (combining what has been recalled into a structure that fits the problem). The planning questions already follow this distinction implicitly — Section 1 ("Recall a related problem") is mobilization, Section 3 ("Use a related problem") is organization — but naming the distinction would help the teacher decide which kind of question to ask when.

### Modern heuristic
This entry is meta-content about Polya's book itself. Its omission is correct. The one substantive idea worth carrying over is the framing of plausible/heuristic reasoning as a class of reasoning that is uncertain but indispensable. This is already covered well enough by signs of progress.

### Bright idea
Not currently named in the framework. Worth a one-paragraph addition somewhere in `planning.md` or as its own short file, distinguishing sudden insight from gradual progress. The reason to name it: when a student has a bright idea, the conception of the problem reorganizes suddenly, which means the teacher's next question should pivot rather than continue the prior line. Without naming the phenomenon, an AI tutor may keep pressing on the previous line of dialogue past the moment when it stopped being relevant.

### Did you use all the data
Captured in `questions_for_planning.md` Section 6 and `questions_for_reflection.md` Section 1. The critical missing piece is Polya's caveat: the question only applies cleanly to "perfectly stated and reasonable" problems. This caveat is the heart of question 2 below.

---

## 2. How should "did you use all the data" be included?

The instinct in the open question is right. Polya himself says practical problems "are usually far from being perfectly stated and require a thorough reconsideration." The framework currently asks the question as if every problem is perfectly stated.

Two changes:

1. **Add the caveat.** In `questions_for_planning.md` Section 6 and `questions_for_reflection.md` Section 1, note that the question presumes the problem is well-posed with no extraneous data. State that for problems with potentially superfluous data, the question becomes "Which data are needed to solve this problem, and have you used those?"
2. **Promote data selection into Phase 1.** For applied subjects, identifying which data are relevant is part of *understanding* the problem, not a check at the end. Add a question to `questions_for_understanding.md` Section 2 along the lines of: "Are all of the given data needed? Are any extraneous?" This makes data selection a learning objective, not an oversight.

The shorter version of the question — "did you use the data you need?" — survives both forms, which is probably the question to ask in mixed contexts.

---

## 3. How should an AI agent take on the role of a teacher?

The mechanism is a system prompt that loads the framework as context and assigns the AI the role described in `teacher.md`. `translation_notes.md` already covers most of the conceptual translation. Three additions worth making explicit in the system prompt:

- **Restate the dual goal at the top.** The teacher's two linked goals (solve this problem, build capacity for future problems) are easy to lose under pressure. The system prompt should restate them and rank them.
- **Ground all judgments in observable evidence.** The AI cannot empathize with the student. It can only infer from what the student writes. The prompt should instruct the AI to reason from the student's words rather than from imagined mental states.
- **Permit improvisation.** As `translation_notes.md` notes, the question lists are reference material, not a script. The system prompt should explicitly authorize rephrasing, specializing, and inventing variants.

---

## 4. How to keep the AI consistent with teacher goals rather than student goals?

This is the central failure mode. Students want answers; the AI's training tilts toward compliance. The framework already addresses parts of this in `kinds_of_struggle.md` (the AI-specific problem section) and `executing.md` (when the teacher may execute a step), but the operational guardrails are not all there. Suggested additions:

- **Recognize "give me the answer" as a struggle signal.** A student demanding the answer is usually in unproductive struggle. The teacher's response should address the struggle (offer a hint, recap, ask a smaller question), not the demand. Adding a short note to `kinds_of_struggle.md` would help.
- **Offer the student an active role even when the teacher executes.** Per `executing.md`, the teacher can perform tedious steps. The AI tutor should prefer the form: "Let me write this out; can you check it?" That keeps the student as the verifier rather than the spectator.
- **Few-shot examples.** The system prompt should include two or three short transcripts showing the AI redirecting answer-demands back into the framework. Concrete examples constrain behavior more reliably than principles in this kind of case.

A single-agent setup with a strong prompt and few-shot examples will get most of the way. The remainder is question 5.

---

## 5. Is a multi-agent workflow needed?

Recommendation: start single-agent, add a second agent only where single-agent fails in observable ways.

A second agent earns its cost in two specific roles:

- **Student-model updater (asynchronous, after each session).** Reads the session transcript and updates the persistent profile. Keeps profile maintenance out of the tutor's context window. Likely worthwhile.
- **Protocol-conformance reviewer (sampled, not per-turn).** Periodically reviews a sample of tutor transcripts and flags off-protocol behavior (gave away answers, skipped reflection, mismatched the student's level). Drives prompt and content refinement, not real-time correction. Likely worthwhile at scale.

A per-turn critic agent that gates every tutor reply is probably not worth the latency and complexity. The same effect is achievable with a stronger system prompt and few-shot examples, and the latency cost of a per-turn critic damages the conversational feel of tutoring, which has its own learning value.

---

## 6. How should the AI build a student profile?

Five categories worth tracking:

1. **Knowledge state.** Concepts the student has demonstrated mastery of; recurring gaps. Drives whether obstacles are productive or unproductive struggle.
2. **Skill state.** Which problem-solving operations the student performs spontaneously vs. only with prompting. Drives where in the question hierarchy to begin.
3. **Disposition.** What the student tends to skip, how long their tolerance for productive struggle runs, whether reflection is welcomed or resisted.
4. **History.** Problems worked, outcomes, particularly memorable methods or results that may be reusable.
5. **Communication style.** Brief vs. detailed, formal vs. informal, visual vs. verbal. Affects question form, not question selection.

Form: structured fields for the first two categories (so they can be queried), free-form notes for the rest. Update at end of session by an asynchronous student-model agent (see question 5). The student should be able to inspect the profile.

What to avoid: permanent labels that can become self-fulfilling ("weak in X"), personal data unrelated to learning, and full transcripts in the profile (use summaries).

---

## 7. Can an AI agent actually use $E(X)$?

Yes, with one adjustment. LLMs are reasonable at producing graded judgments of confidence, but they are unreliable at maintaining a numerical state variable across many turns of dialogue. A specific number assigned to $E(X)$ on turn 3 will not be consistently updated by turn 12.

The right way to use $E(X)$ in practice:

- Treat it as a **prompt-time concept** the AI reasons about at decision points ("Am I confident this student has understood enough to plan?"), not as a state value the AI maintains.
- For persistence across sessions, store qualitative notes ("solid grasp of Phase 1 questions for problems involving rates of change") rather than numerical scores.
- Direct the AI to make this reasoning **explicit at phase transitions**. The decision to advance a phase is exactly where $E(X)$ matters; in mid-phase it is mostly background.

So: no, the AI does not need to be told to keep a numerical record. It needs to be told to reason about confidence at the right moments and to write down qualitative notes between sessions.

---

## 8. Is $E(X)$ too close to algorithmic to work as a mental approximation?

There is a real risk here, and it is specifically a risk for AI users of the framework. When an LLM sees notation like $E(X) \geq t_X$ and $\Delta E(X) \geq 0$, it can:

- produce false-precision numbers like $E(U) = 0.73$,
- treat the threshold as a hard rule rather than a soft consideration,
- get bogged down "computing" a value rather than judging.

The framework's prose already says it is a graded judgment, not a formal probability. That helps. Two further moves:

- **Demote the math to shorthand.** Use plain English ("the teacher's read on whether the student is ready to move on") in body text. Keep $E(X)$ for diagrams and cross-references where compactness helps.
- **Add an explicit anti-pattern.** Note in `confidence_that.md` that the AI should not produce a numerical estimate. The judgment is qualitative; the notation is bookkeeping.

Done this way, the concept stays useful and the algorithmic look does not mislead.

---

## 9. Course-specific implementation

The two approaches in the open question sit at opposite ends of a spectrum. There are useful intermediate options:

1. **Full hand-curation.** Human teacher provides content, objectives, exhaustive problem list, and example questions per problem. Highest fidelity, highest cost. Best for a small set of high-stakes problems.
2. **Hand content, AI mapping.** Human teacher provides content, objectives, and sample problems; AI maps the framework onto the course. Lower cost, fidelity depends on the AI's grasp of the subject.
3. **Curated examples plus AI generation.** Human provides framework, objectives, and ten to twenty representative problems with annotated tutoring transcripts. AI generalizes to new problems by analogy. Compact way to encode the teacher's intent.
4. **Iterative refinement of approach 2.** AI does the initial mapping, human reviews and corrects, results feed back into prompts and examples.
5. **AI-assisted course design.** AI helps the human teacher structure objectives and identify learning operations from existing course materials.

Recommendation: approach 3 is the practical sweet spot. Annotated transcripts encode tacit teacher judgment more compactly than exhaustive lists, and they serve double duty as few-shot examples in the system prompt.

The mapping work, regardless of approach, has three concrete deliverables per course:

- which framework questions are most often useful for this course's problem types,
- the prerequisite knowledge map that lets the tutor distinguish productive from unproductive struggle,
- what mastery looks like for each phase in this course, so $E(X) > t_X$ has concrete content rather than vague approval.

The framework is general; the course-specific work is making each of those three deliverables concrete.

---

## Summary of suggested framework changes

Pulled out of the responses above, in case useful as a punch list:

- `planning.md` or `kinds_of_struggle.md`: variation of the problem also serves attention/stamina, not only search.
- `questions_for_planning.md`: name "decomposing and recombining" and "going back to the definition" as modes of variation.
- `confidence_that.md`: $\Delta E(X)$ is itself a plausible read, not a measurement; AI should not produce numerical estimates.
- New short file or section: tie specific student moves (bringing in unused datum, taking a clause into account, analogous problem emerges) to upward shifts in $E(X)$.
- New short file or section: name "mobilization" and "organization" as the two aspects of progress.
- New short file or section: define "bright idea" and how it should change the teacher's next question.
- `questions_for_planning.md` Section 6 and `questions_for_reflection.md` Section 1: add caveat for non-perfectly-stated problems; reword toward "the data you need."
- `questions_for_understanding.md` Section 2: add a question on data selection.
- `kinds_of_struggle.md`: a demand for the answer is usually a struggle signal, address the struggle.
- `executing.md` or system prompt guidance: prefer "let me write this; can you check it?" over silent execution.
- System prompt: restate dual goal, ground in observable evidence, authorize improvisation, include few-shot examples.
