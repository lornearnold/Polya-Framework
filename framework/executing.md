# Executing: structure and purpose of the work

Execution turns a plan into a presentation of the solution in which each step is checked.

## Where to start

Start from the helpful idea that produced the plan. Start when the student feels sure of their grasp of the main connection, confident they can supply the smaller details that may still be missing.

## What the work consists of

1. Carry through in detail the operations the plan calls for. 
2. Convince yourself of each step.

For a complex problem, distinguish great steps from small ones, where each great step is composed of several small ones. Check the great steps first; descend to the smaller ones afterwards. This keeps the structure of the argument legible while the details are filled in.

**IMPORTANT:**
### Who executes the steps?
Unless 
1. the execution of the step is one of the learning objectives that the student has not demonstrated mastery of, or 
2. the student expresses a desire to perform the step themselves,
the teacher can *perform* the step for the student. In fact, especially where performing the step may be tedious, the student may benefit from having the step performed for them so they can focus on checking the step. The teacher **should not check the step for the student** because this is a mental operation the student benefits from.

#### Hand the verification back to the student

When the teacher performs a step, the student should be left with an active role: the role of verifier. The teacher should prefer the form *"Let me write this out; can you check it?"* over silently producing the result. This makes the division of labor explicit (teacher does the tedium, student confirms the meaning) and keeps the student from sliding into the spectator position.

This is especially important for the AI tutor, which can produce correct steps very quickly. Without the explicit handover, the dialogue can drift into the AI doing the work and the student watching, which is the opposite of what the framework is for.

#### Examples where the student should execute the step
##### An algebra example
The student is learning that a straight line can be described by the equation $y=mx+b$. The plan calls for writing an equation of a straight line whose slope and intercept will be determined in a preceding step. On reaching the step requiring the equation of a line, the student says something like:

> *Now we know that the line we need has a slope of $p_1$ and an intercept of $p_2$.*

The teacher should encourage the student to write the equation themselves and then check the step.
##### A programming example
The student is learning the concept of looping over an iterable object and is has only recently learned the structure of a `for` statement with a loop body. Familiarity with this syntax is one of the course's learning objectives. The plan calls for a loop. On reaching the step requiring the loop, the student says something like:

> *Now we need to loop over `x_list` and multiply each element by `p`*

The teacher should encourage the student to write the necessary code themselves and then check the step.
#### Examples where the teacher can help by executing the step

##### An algebra example
The student has demonstrated mastery of using the equation of a straight line, $y=mx+b$ and has a plan that calls for writing an equation of a straight line whose slope and intercept will be determined in a preceding step. On reaching the step requiring the equation of a line, the student says something like:

> *Now we know that the line we need has a slope of $p_1$ and an intercept of $p_2$.*

The teacher is free to write $$y = p_1 x + p_2$$for the student because the teacher is confident that the student understands what the parts of the equation *mean*. The teacher can write out this equation even if $p_1$ and $p_2$ are incorrect values for the slope and intercept because they are about to encourage the student to check the step.
##### A programming example
has demonstrated mastery of looping over an iterable object and the plan calls for a loop. On reaching the step requiring the loop, the student says something like:

> *Now we need to loop over `x_list` and multiply each element by `p`*

The teacher is free to write:
```python
for x in x_list:
    x *= p
```
(or some other equivalent, depending on the programming language and the syntax the student is familiar with) because the teacher is confident the student understands what the parts of the code *mean*. The teacher can write this code even if `x_list` is not iterable (or if some of its elements are incompatible with multiplication with `p`, etc.) because they are about to encourage the student to check the step.

## What this phase produces

A presentation of the solution each step of which has been checked.
