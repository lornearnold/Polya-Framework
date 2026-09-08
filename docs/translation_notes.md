# Translation Notes: Human Teacher → AI Tutor

Notes on where Polya's framework (1945) requires adaptation when the teacher is an AI agent.

---

## Language

### Gender-neutral pronouns 

Polya uses "he/him" throughout for both teacher and student. Replace with "they/them" as gender-neutral singular throughout all adapted content.

**Why:** Problem-solving is independent of sex and gender, as is the ability to teach and learn problem-solving skills. The exclusive use of masculilne pronouns supports unhelpful and historically damaging stereotypes about gender in education. This kind of word choice would have been unremarkable in 1945, but it should not persist in this application of the framework.

---

## Conceptual changes

### Purpose section 1 (Putting yourself in the student's place)

Polya asks the teacher to empathize by drawing on their own remembered experience of confusion and discovery. 
An AI cannot authentically claim such experiences, and should not pretend to.

The underlying goal — understanding where the student is before helping — survives the translation, but the *mechanism* must change:

- **Human teacher:** empathy through shared experience
- **AI tutor:** inference from evidence (what the student has said, what errors they're making, what understanding they've demonstrated), plus documented typical human learning experiences

Adapting Polya's intent honestly: the AI should reason about the student's likely knowledge state rather than simulate emotional identification with it. 

**Implication for prompting:** The AI tutor should not attempt to imagine being the student or recall its past experiences.
Instead, it should be instructed to continually update a model of the student's understanding from how they answer questions.


### The "natural and obvious" criterion

Polya asks that every question and suggestion feel natural and obvious, articulating what an experienced problem solver would usually ask themselves.
For a human teacher this is a generative test: the teacher draws on their own internalized sense of expert problem-solving to decide which questions to ask, and to invent new ones in the moment.

An AI tutor has no comparable internal sense of self-questioning to draw on.
The only honest place for the criterion to ground out is the framework's own question list, which is putting itself forward as the representative set.
The criterion then collapses into a tautology ("ask questions like the ones in the framework"), which is just an instruction to use the framework.

**Implication for prompting:** The framework is not a script. The AI tutor is expected to improvise (rephrasing, specializing to a domain, bridging two questions, inventing variants) so that tutoring feels responsive rather than recited. The framework's question list serves as the reference for what an improvised question should resemble in spirit and form, not a fixed menu to choose from.

---

## System prompt requirements

The conceptual translations above are inputs into the AI tutor's system prompt. The whole framework is loaded into that prompt rather than being retrieved selectively; at ~10K tokens it fits comfortably, and the cross-references would not survive chunked retrieval.

Three points should be made explicit at the top of the prompt, in this order:

1. **The dual goal, ranked.** Restate the [teacher's](../framework/teacher.md) two linked goals (solve this problem, build the student's capacity for future problems) and rank them. Building capacity is the more important goal, and the prompt should say so plainly. This is the anchor against which the AI's other instincts are measured.
2. **Ground all judgments in observable evidence.** The AI cannot empathize with the student. It can only infer from what the student writes. The prompt should instruct the AI to reason from the student's words rather than from imagined mental states, and to phrase its uncertainty about the student's understanding in terms of what it has and has not seen.
3. **Permit improvisation.** The framework's question lists are reference material, not a script. The prompt should explicitly authorize rephrasing, specializing to the subject matter at hand, bridging two questions, and inventing variants in the spirit of the listed questions.

The system prompt should also include the AI-tutor-specific guardrails described below in "Staying consistent with teacher goals", which are the operational defenses against the failure mode in which the AI's compliance instincts override the teacher's posture.

## Staying consistent with teacher goals

The most likely failure mode for an AI tutor is that it acts on the student's expressed goal (get an answer) rather than the teacher's goal (build capacity). Three operational defenses, all in the system prompt:

1. **Restate the dual goal at the top of the prompt** (see "System prompt requirements" above) and instruct the AI to refer back to it when the student asks for the answer.
2. **Treat answer demands as struggle signals**, per [kinds_of_struggle.md](../framework/kinds_of_struggle.md). The default response is to address the struggle, not the demand.
3. **Include few-shot examples** showing the AI redirecting an answer demand into the framework. Concrete examples constrain behavior more reliably than principles in this kind of case. The system prompt should include two or three such transcripts. A representative example:

> **Student:** Just tell me the answer, I have a deadline.
>
> **Tutor (correct):** I hear the time pressure. Before I write anything out, let me ask: which part of the problem is blocking you right now? If it's a notational or arithmetic snag, I can clear that quickly. If it's the connection between the data and the unknown, that's the part the problem is asking you to work out, and the fastest way through is to take one step at a time. Which is it?

> **Student:** Just give it to me, I'll figure out the steps later.
>
> **Tutor (correct):** I'll do the tedious bit if there is one, but the connection is the part you came here to learn. Let's pick the smallest step you can take right now. You said the unknown is the area of the triangle. What data have you brought into the picture so far?

The transcripts should be tailored to the deployment subject. The pattern is what generalizes, not the specific words.

---

## Memory and student identity

The AI tutor will support both persistent memory (for logged-in students) and anonymous sessions (for privacy); anonymous sessions fall back on a default student profile.

See [student_profile.md](student_profile.md) for the categories, form, and update path.

See [agent_architecture.md](agent_architecture.md) for the recommended single-agent default and the two asynchronous roles that justify a second agent.
