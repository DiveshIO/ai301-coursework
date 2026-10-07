# Procedure: how this skill grades a plan package

<!--
THIS IS THE PART YOU WRITE, and it is a new kind of part. Weeks 1 and
2, SKILL.md carried a numbered workflow and you only wrote judgment
files. This week the workflow is gone from the frame: SKILL.md says
"execute procedure.md", and these are the operating steps you author.
The machinery is in your hands now.

Your operator swap is the design brief. When your executor stalled
because your rubric said WHAT to decide but not HOW to find the
evidence, that was a procedure gap. This file is where those gaps get
closed: a complete procedure lets someone who has never seen a plan
package before (a groupmate, or the skill itself) grade one exactly the
way you would.

Under each stage heading below, write the concrete steps for that
stage. The one-line note under each heading says what a complete
procedure must decide there. Write steps, not intentions: "read the
repro evidence before the plan, and note what behavior it pins down"
is a step; "understand the context" is a wish.
-->

## Read order

<!-- What gets read, in what order, before any check is graded, and
what to note down from each part while reading. A complete procedure
decides the order (issue first? repro evidence first?) and says why
the order matters for the checks that come later. -->
1. Read the issue first and note the reported problem.
2. Read the reproduction evidence and note what was actually tested and what happened.
3. Read the repo-facts and note the repo rules that affect the change or comment.
4. Read `plan.md` and compare its diagnosis, scope, cause, steps, tests, risks, and Deviations with the evidence.
5. Read `comment.md` and compare it with the issue thread and repo rules.

## Evidence gathering

<!-- For each evidence family your rubric's checks name, the concrete
gathering move: which part of the package (or, live, which page or
thread location per your evidence guide) to pull the fact from, and
what to record. A complete procedure leaves no check whose evidence an
executor would have to hunt for. -->

1. For diagnosis, use the plan's diagnosis and the reproduction evidence. Check that the diagnosis matches what was actually observed.
2. For scope, use the plan's scope statement and file list. Check what will and will not be changed.
3. For cause, use the plan's diagnosis and planned fix together with the reproduction evidence. Check that the fix addresses the cause shown by the evidence.
4. For execution, use the plan's files, approach, and implementation steps. Check that another developer can start the work without guessing.
5. For testing, use the plan's test plan and compare it with the reproduction steps and results. Check that the expected result can show whether the fix worked.
6. For honesty, use the plan's risks, unknowns, and `## Deviations` section. Check that unknown things are not presented as facts.
7. For conventions, use the plan comment, issue thread, and repo-facts. Check that the comment follows the repo rules and includes required disclosure.

## Check execution

<!-- How one check runs against gathered evidence: in what order the
checks execute, what an executor does when evidence for a check is
genuinely absent, and when a check may be graded without re-reading
the whole package. A complete procedure makes two executors grade the
same package the same way. -->

1. Run each check in the order listed in `rubric.md`.
2. Use only the evidence gathered for that check and the check's pass condition.
3. Mark the check `pass` when the pass condition is met.
4. Mark the check `fail` when the pass condition is not met.
5. Mark the check `unclear` when there is not enough evidence to decide.
6. Treat `unclear` as `fail`.
7. Do not give a pass because the plan sounds good. The evidence must support the pass condition.


## Verdict assembly

<!-- How the per-check grades become the final accept or reject:
apply your rubric's verdict rule, state how unclear grades enter it,
and say what gets quoted in the output for the deciding check. A
complete procedure produces the same verdict from the same grades,
every time. -->


1. Collect the result for every required check.
2. If every required check is `pass`, the verdict is `accept`.
3. If any required check is `fail`, the verdict is `reject`.
4. If any required check is `unclear`, the verdict is `reject`.
5. For a rejected plan, report which check failed and the evidence that caused the failure.