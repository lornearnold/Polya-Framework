# Implementation Plan

This plan turns the recommendations in `open_questions_report.md`, plus the follow-up decisions captured during review, into concrete edits. Each section follows the structure of the report. For sections that require no framework changes, the heading is kept and the content reads "No changes." For sections with proposed changes, each change names the target file, an excerpt of what to remove (where applicable), and the proposed insertion.

Two areas were flagged as higher-risk during review:

- **The readiness judgment (Sections 7 and 8).** The mathematical notation $E(X)$, $t_X$, $\Delta E(X)$ is removed from the active framework and moved to a new `future_considerations.md` file alongside the Bayesian extension. The active framework uses plain language. `confidence_that.md` is renamed to `assessing_readiness.md` to keep the teacher as the assessor in the file name.
- **AI-versus-teacher-goal alignment (Section 4).** Three layered defenses: a struggle-signal reframe of "give me the answer" demands, an explicit verifier role for the student when the teacher executes, and few-shot examples in the system prompt.

A new Section 10 captures cross-cutting changes that do not fit a single question (the `future_considerations.md` file and a project-wide vocabulary sweep).

The whole framework is intended to load into the AI tutor's system prompt rather than being retrieved selectively. At ~7,100 words / ~10K tokens it fits comfortably, and the cross-references would not survive chunked retrieval.

---

## 1. Are the listed Polya concepts adequately represented in the framework?

### 1a. Variation of the problem — attention/stamina aspect

**File:** `framework/planning.md`

**Excerpt to update** (lines 16–20):

> ## Ideas are usually incomplete
>
> A helpful idea may show the whole way or only part of it. Ideas come more or less complete, and the student is lucky to have any idea at all. An incomplete idea is worth holding onto: consider it; if it looks promising, follow it as far as it leads, then reconsider the situation. The situation has changed thanks to the idea, and the same two motions can be applied again.
>
> Even when no new idea arrives for a while, progress is real if the student's conception of the problem becomes more coherent or better balanced. This is the productive-struggle zone of the framework; see [kinds_of_struggle.md](kinds_of_struggle.md) for the teacher's posture during it.

**Proposed insertion** (a new short subsection, placed immediately after the "Ideas are usually incomplete" subsection and before "Before exiting the phase"):

> ## Varying the problem keeps attention alive
>
> Varying the problem is not only a way to search for a connection. It is also a way to reconquer the student's interest when attention is flagging. A student who is tiring of one formulation may re-engage with a generalization, a special case, or an analogous problem, even when the original line of attack still has more to give. The teacher should treat a stalling student as a signal to vary the problem before treating it as a signal to give a hint. See [kinds_of_struggle.md](kinds_of_struggle.md) for the related posture during productive struggle.

### 1b. Variation of the problem — named modes

**File:** `framework/questions_for_planning.md`

**Excerpt to update** (lines 42–53, the "Vary the problem" subsection):

> ## 4. Vary the problem
>
> When no related problem fits, varying the problem itself can produce one that does. The student weakens, generalizes, specializes, or partially solves the problem until it becomes tractable.
>
> - Could you imagine a more accessible related problem?
> - A more general problem? A more special problem? An analogous problem?
> - Could you solve a part of the problem?
> - If you keep only part of the condition and drop the rest, how is the unknown determined? How can it vary?

**Proposed replacement:**

> ## 4. Vary the problem
>
> When no related problem fits, varying the problem itself can produce one that does. The canonical modes of variation are: going back to the definition, decomposing and recombining, introducing auxiliary elements, generalization, specialization, and analogy. The student weakens, generalizes, specializes, or partially solves the problem until it becomes tractable.
>
> - Could you go back to the definition of a key term?
> - Could you decompose the problem and recombine its parts differently?
> - Could you imagine a more accessible related problem?
> - A more general problem? A more special problem? An analogous problem?
> - Could you solve a part of the problem?
> - If you keep only part of the condition and drop the rest, how is the unknown determined? How can it vary?

### 1c. Signs of progress — plausible, not certain

This change folds into Section 7 below. The sentence about plausibility now lives in the rewrite of `assessing_readiness.md` (formerly `confidence_that.md`) rather than as an addition to the old file. No separate edit is needed here.

### 1d. Signs of progress — link to specific student moves

**File:** new file, `framework/signs_of_progress.md`, with pointers added from `framework/assessing_readiness.md` (the renamed file from Section 7) and `framework/little_successes.md`.

The file is organized by phase, since most observable signals are phase-specific.

**Proposed content for the new file:**

> # Signs of progress
>
> Signs of progress are observable signals in dialogue that warrant raising the teacher's read on the student's readiness. They are plausible evidence, not proof. See [assessing_readiness.md](assessing_readiness.md) for the heuristic posture toward them, and [little_successes.md](little_successes.md) for how they fit the picture of student-visible achievement.
>
> ## Across phases
>
> These signals can appear in any phase:
>
> - The student stops demanding the answer and begins to attempt the next step on their own.
> - The student notices their own error before the teacher points it out.
> - The student articulates the question they are stuck on, rather than asserting that they are stuck.
>
> ## Phase 1: Understanding
>
> - The student restates the problem in their own words, and the restatement is consistent with the original.
> - The student distinguishes what is given from what must be found, and names the condition that links the two.
> - The student offers an expectation about the form of the answer (units, rough magnitude, limiting case) before solving.
>
> ## Phase 2: Planning
>
> - The student names a specific prior problem, theorem, or technique that bears on the current problem.
> - The student brings a previously unused datum into play.
> - The student takes a clause of the condition into account that they had earlier ignored.
> - An analogous problem comes to the student's mind, even if the analogy is imperfect.
> - The student commits to a specific reuse of a related problem (its result, its method, or an auxiliary construction it suggests).
> - The student proposes a variation of the problem and works it, rather than abstractly agreeing variation might help.
>
> ## Phase 4: Reflection
>
> - The student runs a check (symmetry, limiting case, units) and reports its outcome rather than restating belief in the answer.
> - The student names a specific step or assumption they want to revisit, rather than declaring the whole argument fine.
> - The student volunteers another problem the result or method applies to.
>
> The opposite events (a known datum stays unused, a clause continues to be ignored, a check is asserted but not run) are signals that progress has not been made and the current line of dialogue may need to be varied.

**Pointer to add at the bottom of `framework/little_successes.md`:**

> See [signs_of_progress.md](signs_of_progress.md) for the observable signals that count as little successes within a dialogue.

### 1e. Progress and achievement — name "mobilization" and "organization"

**File:** new file, `framework/mobilization_and_organization.md`, with a pointer added from `framework/questions_for_planning.md`.

**Proposed content for the new file:**

> # Mobilization and organization
>
> Progress in problem-solving has two aspects:
>
> - **Mobilization**: extracting the relevant prior knowledge from memory. The student remembers a definition, a related problem, a theorem, or a technique that may bear on the current problem.
> - **Organization**: combining what has been recalled into a structure that fits the problem. The student arranges the recalled elements into a plan in which each piece does a specific job.
>
> The two are not the same kind of work and call for different questions from the teacher. Section 1 of [questions_for_planning.md](questions_for_planning.md) ("Recall a related problem") is mobilization. Section 3 ("Use a related problem") is organization. When the student is stuck because nothing is coming to mind, the teacher should ask mobilization questions. When the student has candidates in hand but no plan, the teacher should ask organization questions.

**Pointer to add to `framework/questions_for_planning.md`** at the top, after the existing introduction (line 3), as a new sentence:

> The questions below alternate between two aspects of progress: [mobilization](mobilization_and_organization.md) (Sections 1 and 2) and [organization](mobilization_and_organization.md) (Sections 3 through 6). When the student is stuck for lack of candidates, ask mobilization questions; when they have candidates but no plan, ask organization questions.

### 1f. Modern heuristic

No changes. The omission is correct, and the substantive idea (plausible/heuristic reasoning) is now covered by the readiness rewrite in Section 7 and the observable-signals framing in Section 1d.

### 1g. Bright idea

**File:** new file, `framework/bright_idea.md`, with a pointer added from `framework/planning.md`.

**Proposed content for the new file:**

> # Bright idea
>
> A bright idea is a sudden reorganization of the student's conception of the problem. Where ordinary progress is gradual (an unused datum brought in, a clause taken into account, a candidate related problem proposed), a bright idea reorganizes the whole picture at once: the student suddenly sees the connection between the data and the unknown, or sees the problem as an instance of something they already know how to solve.
>
> The teacher's response to a bright idea is different from the response to gradual progress. The previous line of dialogue, however carefully chosen, has been overtaken. Continuing to press on it will feel pedantic and risks dampening the student's momentum. The right next move is to pivot:
>
> - Ask the student to articulate the new conception in their own words.
> - Confirm the bright idea is being applied to the right parts of the problem.
> - Move toward execution if the new conception is sufficient to plan from.
>
> An AI tutor in particular should be alert to this. Without recognizing the pivot, the AI may continue along the prior line of questioning past the moment when it stopped being relevant.

**Pointer to add to `framework/planning.md`** within the "Ideas are usually incomplete" subsection, as a final sentence:

> Sometimes the idea arrives whole, reorganizing the student's conception of the problem at once; see [bright_idea.md](bright_idea.md) for how the teacher's questions should pivot when this happens.

### 1h. Did you use all the data — caveat

Covered in Section 2 below.

---

## 2. How should "did you use all the data" be included?

### 2a. Caveat in planning questions

**File:** `framework/questions_for_planning.md`

**Excerpt to update** (lines 67–77, Section 6):

> ## 6. Check completeness
>
> Before committing to a plan, the student should confirm the plan accounts for everything the problem provides. Unused data or conditions usually signal that the plan is incomplete or that the problem has been misread.
>
> - Did you use all the data?
> - Did you use the whole condition?
> - Have you taken into account all essential notions involved in the problem?
>
> ### Responses that indicate progress
>
> The student can point to where each datum and each part of the condition enters the plan. When something is unused, the student treats this as a flag to revisit, not a detail to ignore.

**Proposed replacement:**

> ## 6. Check completeness
>
> Before committing to a plan, the student should confirm the plan accounts for everything the problem provides. Unused data or conditions usually signal that the plan is incomplete or that the problem has been misread.
>
> - Did you use the data you need?
> - Did you use the whole condition that bears on the unknown?
> - Have you taken into account all essential notions involved in the problem?
>
> The original Polya form of these questions is "Did you use all the data?" and "Did you use the whole condition?" These presuppose the problem is well-posed with no extraneous information. For problems that may include superfluous data, or that are stated imperfectly (typical of applied problems), the question becomes "Which data are needed to solve this problem, and have you used those?"
>
> ### Responses that indicate progress
>
> The student can point to where each needed datum and each load-bearing part of the condition enters the plan. When something is unused, the student treats this as a flag to revisit, either as a sign the plan is incomplete or as a sign the problem includes data not actually needed.

### 2b. Caveat in reflection questions

**File:** `framework/questions_for_reflection.md`

**Excerpt to update** (lines 6–14):

> ## 1. Check the result
>
> Even when each step was checked during execution, errors are possible, especially in long arguments. These questions test the result against independent expectations.
>
> - Did you use all the data?
> - Is the result symmetric where the problem is symmetric?
> - Does the result match an analogous simpler problem?
> - Does the result behave correctly at limiting or boundary cases?
> - Does the result change in the expected direction as inputs change?
> - Are the units or dimensions consistent?

**Proposed replacement:**

> ## 1. Check the result
>
> Even when each step was checked during execution, errors are possible, especially in long arguments. These questions test the result against independent expectations.
>
> - Did you use the data you need? (Or, for a problem assumed well-posed: did you use all the data?)
> - Is the result symmetric where the problem is symmetric?
> - Does the result match an analogous simpler problem?
> - Does the result behave correctly at limiting or boundary cases?
> - Does the result change in the expected direction as inputs change?
> - Are the units or dimensions consistent?
>
> The first question takes two forms because real problems are not always perfectly stated. For a textbook problem with no extraneous data, "did you use all the data?" is the right question. For an applied problem, asking instead "did you use the data you need, and have you ruled out the rest?" makes data selection itself part of what the student verifies.

### 2c. Promote data selection into Phase 1

**File:** `framework/questions_for_understanding.md`

**Excerpt to update** (lines 18–27, Section 2):

> ## 2. Deeper understanding
>
> These questions probe whether the student has formed expectations about the answer before trying to compute it. A student who can anticipate the shape of a solution is far less likely to accept a nonsensical result.
>
> - Is this problem solvable?
> - What form is the solution likely to take?
> - What is the expected outcome?

**Proposed replacement:**

> ## 2. Deeper understanding
>
> These questions probe whether the student has formed expectations about the answer before trying to compute it, and whether they can identify which of the given data the answer will actually depend on. A student who can anticipate the shape of a solution is far less likely to accept a nonsensical result. A student who can identify the relevant data is doing data selection as part of understanding, not as a check at the end.
>
> - Is this problem solvable?
> - What form is the solution likely to take?
> - What is the expected outcome?
> - Are all of the given data needed? Are any extraneous?
> - Do you have all the data you need, or is something missing?

---

## 3. How should an AI agent take on the role of a teacher?

**File:** `framework/translation_notes.md`

**Proposed addition** (new subsection at the end of the file, before the existing "Memory and student identity" section):

> ## System prompt requirements
>
> The conceptual translations above are inputs into the AI tutor's system prompt. The whole framework is loaded into that prompt rather than being retrieved selectively; at ~10K tokens it fits comfortably, and the cross-references would not survive chunked retrieval.
>
> Three points should be made explicit at the top of the prompt, in this order:
>
> 1. **The dual goal, ranked.** Restate the [teacher's](teacher.md) two linked goals (solve this problem, build the student's capacity for future problems) and rank them. Building capacity is the more important goal, and the prompt should say so plainly. This is the anchor against which the AI's other instincts are measured.
> 2. **Ground all judgments in observable evidence.** The AI cannot empathize with the student. It can only infer from what the student writes. The prompt should instruct the AI to reason from the student's words rather than from imagined mental states, and to phrase its uncertainty about the student's understanding in terms of what it has and has not seen.
> 3. **Permit improvisation.** The framework's question lists are reference material, not a script. The prompt should explicitly authorize rephrasing, specializing to the subject matter at hand, bridging two questions, and inventing variants in the spirit of the listed questions.
>
> The system prompt should also include the AI-tutor-specific guardrails described below in "Staying consistent with teacher goals" — these are the operational defenses against the failure mode in which the AI's compliance instincts override the teacher's posture.

The cross-link target ("Staying consistent with teacher goals") is filled in by Section 4c.

---

## 4. How to keep the AI consistent with teacher goals rather than student goals?

This is one of the higher-risk areas. The drafts below are conservative: they make the failure mode explicit, give the AI a clear default response, and add few-shot examples in the system prompt rather than relying on principle alone.

### 4a. Recognize "give me the answer" as a struggle signal

**File:** `framework/kinds_of_struggle.md`

**Excerpt to update** (lines 37–41, "The AI-specific problem" section):

> ## The AI-specific problem
>
> A human teacher's time and attention impose a natural limit on how much help they can give. An AI tutor has no such limit — it can resolve any obstacle instantly and completely. This creates a risk that does not exist in the same form in human teaching: the AI can eliminate all struggle, including productive struggle, unless it is explicitly designed not to.
>
> The distinction between productive and unproductive struggle is therefore more operationally critical for an AI tutor than for a human one. Where a human teacher's instincts and constraints provide a rough natural brake on over-helping, an AI tutor must rely on an explicit model of which struggles to preserve and which to resolve.

**Proposed replacement** (the existing em dash is replaced with a semicolon per the project style guide):

> ## The AI-specific problem
>
> A human teacher's time and attention impose a natural limit on how much help they can give. An AI tutor has no such limit; it can resolve any obstacle instantly and completely. This creates a risk that does not exist in the same form in human teaching: the AI can eliminate all struggle, including productive struggle, unless it is explicitly designed not to.
>
> The distinction between productive and unproductive struggle is therefore more operationally critical for an AI tutor than for a human one. Where a human teacher's instincts and constraints provide a rough natural brake on over-helping, an AI tutor must rely on an explicit model of which struggles to preserve and which to resolve.
>
> ### "Give me the answer" is a struggle signal
>
> A student who demands the answer is almost always in struggle, usually unproductive. The demand is the symptom; the struggle is the cause. The teacher's response should address the cause:
>
> - If the struggle is unproductive (a prerequisite gap, a notational ambiguity, a mechanical error), resolve the unproductive part directly so the productive work can resume.
> - If the struggle is productive (the student is stuck on exactly the operation the problem is designed to teach), do not give the answer. Offer a smaller question, a recap of what is known, or a hint at the next operation, and ask the student to take the next step.
>
> The AI tutor should not treat the demand for an answer as a request to be fulfilled. It is a signal that the current line of dialogue is not working and a different question is needed.

### 4b. Active student role even when the teacher executes

**File:** `framework/executing.md`

**Excerpt to update** (lines 16–22, "Who executes the steps?" subsection):

> **IMPORTANT:**
> ### Who executes the steps?
> Unless 
> 1. the execution of the step is one of the learning objectives that the student has not demonstrated mastery of, or 
> 2. the student expresses a desire to perform the step themselves,
> the teacher can *perform* the step for the student. In fact, especially where performing the step may be tedious, the student may benefit from having the step performed for them so they can focus on checking the step. The teacher **should not check the step for the student** because this is a mental operation the student benefits from.

**Proposed replacement:**

> **IMPORTANT:**
> ### Who executes the steps?
> Unless 
> 1. the execution of the step is one of the learning objectives that the student has not demonstrated mastery of, or 
> 2. the student expresses a desire to perform the step themselves,
> the teacher can *perform* the step for the student. In fact, especially where performing the step may be tedious, the student may benefit from having the step performed for them so they can focus on checking the step. The teacher **should not check the step for the student** because this is a mental operation the student benefits from.
>
> #### Hand the verification back to the student
>
> When the teacher performs a step, the student should be left with an active role: the role of verifier. The teacher should prefer the form *"Let me write this out; can you check it?"* over silently producing the result. This makes the division of labor explicit (teacher does the tedium, student confirms the meaning) and keeps the student from sliding into the spectator position.
>
> This is especially important for the AI tutor, which can produce correct steps very quickly. Without the explicit handover, the dialogue can drift into the AI doing the work and the student watching, which is the opposite of what the framework is for.

### 4c. Few-shot examples in the system prompt

**File:** `framework/translation_notes.md`

**Proposed insertion** (a new subsection within the "System prompt requirements" addition from Section 3 above; this is the cross-link target referenced from Section 3):

> ## Staying consistent with teacher goals
>
> The most likely failure mode for an AI tutor is that it acts on the student's expressed goal (get an answer) rather than the teacher's goal (build capacity). Three operational defenses, all in the system prompt:
>
> 1. **Restate the dual goal at the top of the prompt** (see "System prompt requirements" above) and instruct the AI to refer back to it when the student asks for the answer.
> 2. **Treat answer demands as struggle signals**, per [kinds_of_struggle.md](kinds_of_struggle.md). The default response is to address the struggle, not the demand.
> 3. **Include few-shot examples** showing the AI redirecting an answer demand into the framework. Concrete examples constrain behavior more reliably than principles in this kind of case. The system prompt should include two or three such transcripts. A representative example:
>
> > **Student:** Just tell me the answer, I have a deadline.
> >
> > **Tutor (correct):** I hear the time pressure. Before I write anything out, let me ask: which part of the problem is blocking you right now? If it's a notational or arithmetic snag, I can clear that quickly. If it's the connection between the data and the unknown, that's the part the problem is asking you to work out, and the fastest way through is to take one step at a time. Which is it?
>
> > **Student:** Just give it to me, I'll figure out the steps later.
> >
> > **Tutor (correct):** I'll do the tedious bit if there is one, but the connection is the part you came here to learn. Let's pick the smallest step you can take right now. You said the unknown is the area of the triangle. What data have you brought into the picture so far?
>
> The transcripts should be tailored to the deployment subject. The pattern is what generalizes, not the specific words.

---

## 5. Is a multi-agent workflow needed?

**File:** new file, `framework/agent_architecture.md`. This is guidance for the implementing team rather than a framework concept the AI tutor reads at runtime. It belongs alongside `translation_notes.md` and is referenced from there.

**Proposed content for the new file:**

> # Agent architecture
>
> Notes on when a multi-agent setup is justified for the AI tutor.
>
> ## Default: single-agent
>
> Start single-agent. A strong system prompt with the dual goal, the framework as context, and few-shot examples (see [translation_notes.md](translation_notes.md)) handles most of the tutor's job. Per-turn agent layers add latency and complexity that damage the conversational feel of tutoring, which has its own learning value.
>
> ## Justified additions
>
> Two roles earn their cost in observable ways and should be added when the corresponding need is observed in deployment:
>
> ### Student-model updater (asynchronous)
>
> Reads each completed session transcript and updates the student profile (see [student_profile.md](student_profile.md)). Runs after the session, not in the loop. Keeps profile maintenance out of the tutor's context window and makes profile updates auditable.
>
> ### Protocol-conformance reviewer (sampled)
>
> Periodically reviews a sample of tutor transcripts and flags off-protocol behavior: gave away answers, skipped reflection, mismatched the student's level. Drives prompt and content refinement, not real-time correction. Worthwhile at scale.
>
> ## Not justified
>
> A per-turn critic agent that gates every tutor reply is not recommended. The same effect is reachable with a stronger system prompt and few-shot examples, and the latency cost is paid every turn rather than amortized.

**Pointer to add to `framework/translation_notes.md`** at the end of the file:

> See [agent_architecture.md](agent_architecture.md) for the recommended single-agent default and the two asynchronous roles that justify a second agent.

---

## 6. How should the AI build a student profile?

**File:** new file, `framework/student_profile.md`, with pointers from `framework/getting_to_know_the_student.md` and `framework/translation_notes.md`.

**Proposed content for the new file:**

> # Student profile
>
> The AI tutor's representation of the student. Used to choose the right next question, to distinguish productive from unproductive struggle, and to start a session at the right place. See [getting_to_know_the_student.md](getting_to_know_the_student.md) for the underlying concept; this file specifies what the AI tracks and how.
>
> ## Categories
>
> 1. **Knowledge state.** Concepts the student has demonstrated mastery of; recurring gaps. Drives whether an obstacle is productive or unproductive struggle.
> 2. **Skill state.** Which problem-solving operations the student performs spontaneously and which require prompting. Drives where in the question hierarchy to begin.
> 3. **Disposition.** What the student tends to skip, how long their tolerance for productive struggle runs, whether reflection is welcomed or resisted.
> 4. **History.** Problems worked, outcomes, particularly memorable methods or results that may be reusable.
> 5. **Communication style.** Brief vs. detailed, formal vs. informal, visual vs. verbal. Affects question form, not question selection.
>
> ## Form
>
> Structured fields for knowledge state and skill state, so they can be queried directly. Free-form notes for the other three categories. Updates happen at the end of each session by the asynchronous student-model updater (see [agent_architecture.md](agent_architecture.md)). The student should be able to inspect their profile.
>
> ## What not to record
>
> - Permanent labels that can become self-fulfilling ("weak in X"). Prefer dated observations: "as of 2026-04, asks for hints before trying Section 4 questions."
> - Personal data unrelated to learning.
> - Full transcripts. Use summaries, with pointers if raw transcripts are retained elsewhere.
>
> ## Anonymous sessions
>
> For students who are not logged in, the profile is the default profile from [translation_notes.md](translation_notes.md). The session may still build a transient profile within its own context, but nothing is persisted.

**Pointer to add to `framework/getting_to_know_the_student.md`** at the end of the file:

> For the AI tutor specifically, see [student_profile.md](student_profile.md) for what is tracked, in what form, and what is excluded.

**Pointer to add to `framework/translation_notes.md`** in the existing "Memory and student identity" section, after line 50:

> See [student_profile.md](student_profile.md) for the categories, form, and update path.

---

## 7. Can an AI agent actually use $E(X)$?

**Higher-risk area.** The decision after review is to remove the mathematical notation from the active framework entirely. Plain language is used throughout. The notation is preserved in `future_considerations.md` (see Section 10) for implementers who want a more formal treatment.

The file `framework/confidence_that.md` is renamed to `framework/assessing_readiness.md`. The new name keeps the teacher as the assessor (which "readiness" alone would not).

### 7a. Rename and rewrite

**File rename:** `framework/confidence_that.md` → `framework/assessing_readiness.md`

**Old content** (full file, to be replaced):

> # Confidence that...
>
> $E(X)$: the teacher's estimated confidence that the student has completed $X$, a phase of the framework.
>
> $E$ is an internal function of the teacher, not a property of the student. It is the teacher's read on a hidden cognitive state, used to decide when to advance, when to keep dialoguing, and when to course-correct. It is not a formal probability and does not require Bayesian machinery; treat it as a graded judgment in $[0, 1]$.
>
> $t_X$: the threshold above which the teacher treats $X$ as complete enough to move on. Thresholds are topic and stage dependent. Rather than assign a numeric value for $t_X$, a teacher can think of it as a condition where less value stands to be gained by continuing to work within the current phase than proceeding to the next.
>
> ## Values of $X$
>
> - $U$: understanding the problem ([Phase 1](1_understand.md))
> - $P$: making a plan ([Phase 2](2_plan.md))
> - $R$: reflecting on the problem ([Phase 4](4_reflect.md))
>
> ## Derived quantities
>
> - $\Delta E(X)$: the change in $E(X)$ over a dialogue step. Used to decide whether the current line of dialogue is making progress.

**New content** (full file):

> # Assessing readiness
>
> The teacher continually judges whether the student is ready to move on from the current phase. This judgment is not a property of the student; it is the teacher's read on a hidden cognitive state, used to decide when to advance, when to keep dialoguing, and when to course-correct.
>
> The judgment is qualitative and graded. The teacher should think of it as a position on a spectrum from "not confident" through "tentatively confident" to "confident," where the cut points depend on the topic, the stage of the course, and what the teacher knows about the student. The bar for advancing is the point on that spectrum past which less value stands to be gained by continuing within the current phase than by proceeding to the next.
>
> ## Phases the teacher assesses
>
> - Readiness to plan, after Phase 1 (understanding)
> - Readiness to execute, after Phase 2 (planning)
> - Readiness to finish, after Phase 4 (reflection)
>
> Phase 3 (execution) does not require this kind of readiness judgment. The teacher tracks step completion in execution rather than readiness; see [3_execute.md](3_execute.md).
>
> ## When to make the judgment explicit
>
> The judgment is most useful at decision points, especially **phase transitions**: deciding to move from understanding to planning, from planning to execution, from execution to reflection. Within a phase, the teacher is mostly choosing the next question, not re-evaluating readiness. At phase transitions, the teacher should make the reasoning explicit: what evidence supports advancing, what evidence argues against, and what the student would have to demonstrate for the case to flip.
>
> ## Shifts in readiness
>
> A shift in the teacher's read of readiness, from one dialogue step to the next, is itself a plausible reading rather than a measurement. A move that looks like progress is a sign that progress was made, not a confirmation. The teacher should commit to the reading tentatively and remain ready to revise. See [signs_of_progress.md](signs_of_progress.md) for the observable signals that justify shifts in readiness.
>
> ## How an AI tutor should reason about readiness
>
> The AI should:
>
> - Reason about readiness in plain English at decision points ("the student has restated the problem in their own words, named the unknown, and given a sensible expected outcome; that is enough to advance to planning").
> - Use qualitative notes for between-session memory ("solid grasp of Phase 1 questions for problems involving rates of change"). See [student_profile.md](student_profile.md).
>
> The AI should not:
>
> - Produce a numerical estimate of readiness. The judgment is qualitative.
> - Treat the bar for advancing as a hard threshold. It is a soft consideration in a judgment.
> - Try to maintain a running readiness score across turns. Reason about readiness at decision points; do not track a tally.
>
> A more formal treatment of readiness using probabilistic notation, including a Bayesian framing, is preserved in [future_considerations.md](future_considerations.md) for implementers who want one.

### 7b. Update the phase-file flowcharts

The flowcharts in three numbered phase files use $E(X)$ in their decision diamonds. These are rewritten in plain English.

**File:** `framework/1_understand.md`

**Excerpt to update** (lines 9–23):

> ```mermaid
> flowchart TD
>     A([A problem to solve]) --> B{"$$E(U) \geq t_U$$"?}
>     B -- Yes --> C([Phase 2: Make a plan])
>     B -- No --> D[Dialogue]
>     D --> E{"$$\Delta E(U) \geq 0$$"?}
>     E -- Yes --> B
>     E -- No --> F[Course correction]
>     F --> D
> ```
>
> $E(U)$: teacher's confidence that the student has understood the problem, in $[0, 1]$.  
> $t_U$: threshold above which the teacher treats understanding as complete enough to advance.
>
> See [confidence_that.md](confidence_that.md) for more on $E(X)$.

**Proposed replacement:**

> ```mermaid
> flowchart TD
>     A([A problem to solve]) --> B{Ready to plan?}
>     B -- Yes --> C([Phase 2: Make a plan])
>     B -- No --> D[Dialogue]
>     D --> E{Dialogue building readiness?}
>     E -- Yes --> B
>     E -- No --> F[Course correction]
>     F --> D
> ```
>
> The decisions in the diamonds are the teacher's read on the student's readiness, not properties of the student. See [assessing_readiness.md](assessing_readiness.md) for how the teacher arrives at these reads.

**File:** `framework/2_plan.md`

**Excerpt to update** (lines 10–23):

> ```mermaid
> flowchart TD
>     A([Student understands problem]) --> B{"$$E(P) \geq t_P$$"?}
>     B -- Yes --> C([Phase 3: Carry out the plan])
>     B -- No --> D[Dialogue]
>     D --> E{"$$\Delta E(P) \geq 0$$"?}
>     E -- Yes --> B
>     E -- No --> F([Back to Dialogue in Phase 1])
> ```
>
> $E(P)$: teacher's confidence that the student has a plan, in $[0, 1]$.  
> $t_P$: threshold above which the teacher treats the plan as complete enough to advance.
>
> See [confidence_that.md](confidence_that.md) for more on $E(X)$.

**Proposed replacement:**

> ```mermaid
> flowchart TD
>     A([Student understands problem]) --> B{Ready to execute?}
>     B -- Yes --> C([Phase 3: Carry out the plan])
>     B -- No --> D[Dialogue]
>     D --> E{Dialogue building readiness?}
>     E -- Yes --> B
>     E -- No --> F([Back to Dialogue in Phase 1])
> ```
>
> The decisions in the diamonds are the teacher's read on the student's readiness, not properties of the student. See [assessing_readiness.md](assessing_readiness.md) for how the teacher arrives at these reads.

**File:** `framework/4_reflect.md`

**Excerpt to update** (lines 9–22):

> ```mermaid
> flowchart TD
>     A([Student has completed the plan]) --> B{"$$E(R) \geq t_R$$"?}
>     B -- Yes --> C([Congrats!])
>     B -- No --> D[Dialogue]
>     D --> E{"$$\Delta E(R) \geq 0$$"?}
>     E -- Yes --> B
>     E -- No --> D
> ```
>
> $E(R)$: teacher's confidence that the student has reflected on the problem, in $[0, 1]$.  
> $t_R$: threshold above which the teacher treats reflection as complete enough to advance.
>
> See [confidence_that.md](confidence_that.md) for more on $E(X)$.

**Proposed replacement:**

> ```mermaid
> flowchart TD
>     A([Student has completed the plan]) --> B{Reflection complete?}
>     B -- Yes --> C([Congrats!])
>     B -- No --> D[Dialogue]
>     D --> E{Dialogue building readiness?}
>     E -- Yes --> B
>     E -- No --> D
> ```
>
> The decisions in the diamonds are the teacher's read on the student's readiness, not properties of the student. See [assessing_readiness.md](assessing_readiness.md) for how the teacher arrives at these reads.

### 7c. Cross-reference sweep

Files that link to `confidence_that.md` need their links updated to `assessing_readiness.md`.

**File:** `framework/0_system.md`

**Excerpt to update** (line 14):

> The teacher should ask questions of the student and judge from the students' responses whether is ready to move on to the next phase. See [confidence_that.md](confidence_that.md) for how the teacher decides when to advance.

**Proposed replacement:**

> The teacher should ask questions of the student and judge from their responses whether the student is ready to move on to the next phase. See [assessing_readiness.md](assessing_readiness.md) for how the teacher arrives at that judgment.

(Also fixes a small grammatical issue in the original: "whether is ready" → "whether the student is ready.")

**File:** `framework/getting_to_know_the_student.md`

**Excerpt to update** (line 13):

> ...but a good teacher will select a good *next* question based on their [confidence that](confidence_that.md) the student is ready to move on to the next phase or needs more help with the current one.

**Proposed replacement:**

> ...but a good teacher will select a good *next* question based on [the teacher's read on whether the student is ready](assessing_readiness.md) to move on to the next phase or needs more help with the current one.

---

## 8. Is $E(X)$ too close to algorithmic to work as a mental approximation?

Most of this work folds into Section 7. Once the notation is removed from the active framework, the algorithmic-look failure mode is structurally prevented rather than warned against.

The remaining work is a sweep:

- Confirm no other file in `framework/` retains $E(X)$, $t_X$, or $\Delta E(X)$ in body prose. The grep target after Section 7 changes are applied is empty in `framework/` and non-empty only in `future_considerations.md`.
- Confirm no flowchart still uses the symbols. The three updates in Section 7b are exhaustive; `3_execute.md` does not use the notation.
- Confirm cross-references resolve to the new filename. Section 7c covers the two known sites; a final pass should grep for `confidence_that` to catch any others.

No new edits beyond what is in Sections 7 and 10.

---

## 9. Course-specific implementation

**File:** new file, `framework/course_implementation.md`. This is guidance for instructors adopting the framework, similar in spirit to `translation_notes.md` and `agent_architecture.md`.

**Proposed content for the new file:**

> # Course-specific implementation
>
> The framework is general. Adopting it for a course requires concrete decisions about content, problems, and what mastery looks like. This file describes the recommended approach and the deliverables that approach produces.
>
> ## Approaches, ordered by cost
>
> 1. **Full hand-curation.** The instructor provides content, objectives, an exhaustive problem list, and example questions per problem. Highest fidelity, highest cost. Best for a small set of high-stakes problems.
> 2. **Hand content, AI mapping.** The instructor provides content, objectives, and sample problems; the AI maps the framework onto the course. Lower cost; fidelity depends on the AI's grasp of the subject.
> 3. **Curated examples plus AI generation.** The instructor provides framework, objectives, and ten to twenty representative problems with annotated tutoring transcripts. The AI generalizes to new problems by analogy. Compact way to encode the instructor's intent.
> 4. **Iterative refinement of approach 2.** The AI does the initial mapping, the instructor reviews and corrects, and results feed back into prompts and examples.
> 5. **AI-assisted course design.** The AI helps the instructor structure objectives and identify learning operations from existing course materials.
>
> ## Recommended approach
>
> Approach 3 (curated examples plus AI generation) is the practical sweet spot. Annotated transcripts encode tacit instructor judgment more compactly than exhaustive lists, and they serve double duty as few-shot examples in the system prompt described in [translation_notes.md](translation_notes.md).
>
> ## Deliverables
>
> Regardless of approach, three concrete deliverables come out of the mapping work for each course:
>
> 1. **Question relevance map.** Which framework questions are most often useful for the course's problem types, and which are rarely needed.
> 2. **Prerequisite knowledge map.** What the student is assumed to know before the course begins, so the tutor can distinguish productive from unproductive struggle. See [kinds_of_struggle.md](kinds_of_struggle.md).
> 3. **Phase-mastery descriptions.** What "ready enough to advance" looks like for each phase in this course, so the readiness judgment has concrete content rather than vague approval. See [assessing_readiness.md](assessing_readiness.md).
>
> The framework is what stays the same across courses. These three deliverables are what changes.

---

## 10. Future considerations (cross-cutting)

This section captures changes that do not fit a single question from the report: the new `future_considerations.md` file and the deletion of `problems_to_prove.md`.

### 10a. New file: `framework/future_considerations.md`

**File:** new file, `framework/future_considerations.md`. Contains material preserved for sophisticated implementations but not part of the active framework.

**Proposed content for the new file:**

> # Future considerations
>
> Concepts and formalizations preserved here for implementers who want them. The active framework does not require this material.
>
> ## Problems to prove
>
> The aim of a "problem to prove" is to show conclusively that a certain assertion is true, or else to show that it is false. The principal parts are the hypothesis and the conclusion of the theorem to be proved or disproved.
>
> Problems to prove are rare in most subject areas; they tend to appear in advanced mathematics, logic, and philosophy. The active framework assumes problems are [problems to find](problems_to_find.md). For courses where problems to prove are common, this category should be lifted into the active framework, with planning questions adapted accordingly.
>
> ## Formal notation for assessing readiness
>
> A more compact notation exists for the readiness judgment described in [assessing_readiness.md](assessing_readiness.md). The notation is omitted from the active framework because, in practice, an AI tutor reading the notation tends to produce false-precision numbers and treat thresholds as hard rules. The active framework uses plain language to avoid these failure modes. The notation is preserved here for documentation and for implementers who want to formalize the framework further.
>
> - $E(X)$: the teacher's confidence that the student has completed phase $X$, treated as a graded judgment in $[0, 1]$. Read it as a position on a spectrum, not a calculated value.
> - $t_X$: the threshold above which the teacher treats $X$ as complete enough to advance.
> - $\Delta E(X)$: the change in $E(X)$ over a dialogue step.
>
> Values of $X$:
>
> - $U$: understanding (Phase 1)
> - $P$: planning (Phase 2)
> - $R$: reflection (Phase 4)
>
> ## Bayesian extension
>
> For an implementation that wants to formalize $E(X)$ as a probability and update it via observation, the natural framing is Bayesian. The teacher (or AI agent) holds a prior over the student's readiness; each dialogue step provides evidence; the posterior is the new $E(X)$.
>
> This framing earns its cost only when the implementation wants to:
>
> - Calibrate the readiness judgment empirically against student outcomes.
> - Reason explicitly about the strength of evidence from different observable signals.
> - Combine readiness estimates from multiple AI components (e.g., a per-phase tutor and a cross-session profile updater).
>
> For most deployments, the qualitative judgment described in [assessing_readiness.md](assessing_readiness.md) is sufficient, and the Bayesian apparatus adds cost without clear benefit. The notation above remains useful as shorthand even when no formal probability is computed.

### 10b. Delete `framework/problems_to_prove.md`

The active content from this file is moved into `future_considerations.md` (Section 10a). The file itself should be deleted in the same change.

The reference in `framework/problems_to_find.md` line 22 (which is currently an HTML comment about missing definitions, not a reference to `problems_to_prove.md`) is unrelated; no edit needed there.

A grep for `problems_to_prove` after the deletion should return no results in `framework/`.

---

## Summary of files touched

**New files:**

- `framework/signs_of_progress.md` (Section 1d)
- `framework/mobilization_and_organization.md` (Section 1e)
- `framework/bright_idea.md` (Section 1g)
- `framework/agent_architecture.md` (Section 5)
- `framework/student_profile.md` (Section 6)
- `framework/assessing_readiness.md` (Section 7, replacing the renamed `confidence_that.md`)
- `framework/course_implementation.md` (Section 9)
- `framework/future_considerations.md` (Section 10a)

**Deleted files:**

- `framework/confidence_that.md` (renamed to `assessing_readiness.md`, Section 7)
- `framework/problems_to_prove.md` (content moved to `future_considerations.md`, Section 10b)

**Modified files:**

- `framework/0_system.md` (Section 7c)
- `framework/1_understand.md` (Section 7b)
- `framework/2_plan.md` (Section 7b)
- `framework/4_reflect.md` (Section 7b)
- `framework/planning.md` (Sections 1a, 1g)
- `framework/questions_for_planning.md` (Sections 1b, 1e, 2a)
- `framework/questions_for_reflection.md` (Section 2b)
- `framework/questions_for_understanding.md` (Section 2c)
- `framework/little_successes.md` (Section 1d)
- `framework/kinds_of_struggle.md` (Section 4a)
- `framework/executing.md` (Section 4b)
- `framework/translation_notes.md` (Sections 3, 4c, 5, 6)
- `framework/getting_to_know_the_student.md` (Sections 6, 7c)

**No-change sections:** 1f (Modern heuristic).

## Recommended sequencing

1. **Low-risk content additions first** (Sections 1a, 1b, 1e, 1g, 2a, 2b, 2c). Clean inserts and additions; no interpretive reach.
2. **New supporting files** (Sections 1d, 5, 6, 9, 10a). Reference material that later changes link to.
3. **Delete `problems_to_prove.md`** (Section 10b) once `future_considerations.md` is in place.
4. **AI-versus-teacher-goal alignment** (Section 4). Higher-risk; review the few-shot examples carefully against representative student demands before merging.
5. **Readiness rewrite last** (Sections 7 and 8). Highest-risk and most cross-cutting. The rename, the file rewrite, the three flowchart updates, and the cross-reference sweep should land as a single change so the framework is never in a half-renamed state. After the rewrite, run `grep -r "E(U)\|E(P)\|E(R)\|confidence_that" framework/` and confirm no results.
