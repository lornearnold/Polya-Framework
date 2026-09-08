# Future considerations

Concepts and formalizations preserved here for implementers who want them. The active framework does not require this material.

## Problems to prove

The aim of a "problem to prove" is to show conclusively that some premise is true that it is false. The principal parts are the hypothesis and the conclusion of the theorem to be proved or disproved.

Problems to prove are rare in most subject areas; they tend to appear in advanced mathematics, logic, and philosophy. The active framework assumes problems are [problems to find](../framework/problems_to_find.md). For courses where problems to prove are common, this category should be lifted into the active framework, with planning questions adapted accordingly.

## Formal notation for assessing readiness

A more compact notation exists for the readiness judgment described in [assessing_readiness.md](../framework/assessing_readiness.md). The notation is omitted from the active framework because, in practice, an AI tutor reading the notation tends to produce false-precision numbers and treat thresholds as hard rules. The active framework uses plain language to avoid these failure modes. The notation is preserved here for documentation and for implementers who want to formalize the framework further.

- $E(X)$: the teacher's confidence that the student has completed phase $X$, treated as a graded judgment in $[0, 1]$. Read it as a position on a spectrum, not a calculated value.
- $t_X$: the threshold above which the teacher treats $X$ as complete enough to advance.
- $\Delta E(X)$: the change in $E(X)$ over a dialogue step.

Values of $X$:

- $U$: understanding (Phase 1)
- $P$: planning (Phase 2)
- $R$: reflection (Phase 4)

## Bayesian extension

For an implementation that wants to formalize $E(X)$ as a probability and update it via observation, the natural framing is Bayesian. The teacher (or AI agent) holds a prior over the student's readiness; each dialogue step provides evidence; the posterior is the new $E(X)$.

This framing earns its cost only when the implementation wants to:

- Calibrate the readiness judgment empirically against student outcomes.
- Reason explicitly about the strength of evidence from different observable signals.
- Combine readiness estimates from multiple AI components (e.g., a per-phase tutor and a cross-session profile updater).

For most deployments, the qualitative judgment described in [assessing_readiness.md](../framework/assessing_readiness.md) is sufficient, and the Bayesian apparatus adds cost without clear benefit. The notation above remains useful as shorthand even when no formal probability is computed.
