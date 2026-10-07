# Evidence guide: where evidence lives in a plan package

<!--
THIS IS THE PART YOU WRITE (second week running: the judgment files
stay in your hands). The skill uses this guide as its map: for every
kind of evidence a rubric check names, this file says WHERE to find it
in a plan package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repro-evidence block,
  the candidate plan's scope statement or test plan, the plan comment,
  the repo-facts block). In live mode (where on GitHub or in the
  draft: the issue thread, the student's posted repro comment, the
  repo's docs, the draft plan and comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the stated cause cites behavior the
  repro evidence actually shows") over adjectives ("diagnosis is
  solid").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute, and this week that cuts twice: your
procedure.md tells the skill WHEN to gather each family, and this
guide tells it WHERE. Write the map you wish your executor had.
-->
**Where it lives:** The issue, reproduction evidence, and diagnosis in plan.md.

**What good looks like:** The diagnosis matches what the reproduction actually showed. It should not claim something happened when there is no evidence for it.


## Diagnosis and grounding

<!-- Where the plan states its cause, and where the repro evidence
pins down the behavior that cause must explain. What it means for a
diagnosis to follow from the evidence rather than contradict or
ignore it. -->
**Where it lives:** The issue, reproduction evidence, and diagnosis in plan.md.

**What good looks like:** The diagnosis matches what the reproduction actually showed. It should not claim something happened when there is no evidence for it.



## Scope

<!-- Where the plan bounds itself: the in-scope statement, the
not-in-scope line, the files or areas named. What one bounded change
looks like next to a drive-by rewrite. -->

**Where it lives:** The scope and files to change in plan.md.

**What good looks like:** The plan only includes work needed for the issue. Unrelated changes should not be included.


## Executability

<!-- Where the plan says what will actually be done: files or areas,
approach, order of work. What it means for a stranger to be able to
start executing without asking the author anything. -->
**Where it lives:** The files, approach, and steps in plan.md.

**What good looks like:** Someone else should be able to start the work from the plan without asking what to do next.

## Test plan

<!-- Where the plan says how success will be observed, and how that
maps onto the repro evidence's steps and artifacts. What a decisive
test plan names that a vague one does not. -->
**Where it lives:** The reproduction evidence and test plan in plan.md.

**What good looks like:** The plan tests the real code and says what result should happen if the fix works.

## Honesty

<!-- Where claims meet uncertainty: risks, unknowns, and deviations.
How to tell stated unknowns from false confidence, and where an
honest mid-build deviation gets recorded. -->
**Where it lives:** The diagnosis, risks, unknowns, and `## Deviations` in plan.md.

**What good looks like:** The plan does not pretend something is known when it is not. Unknowns should be written down. If the plan changes during the work, explain it in Deviations.

## Comms

<!-- Where the words meet the thread and the repo: the plan comment
read against the issue's maintainer signals (thread highlights, or
the live thread) and against the repo-facts block's stated templates,
contributing asks, and contribution policy (including AI-use
disclosure requirements). What thread-aware looks like next to
boilerplate. -->
**Where it lives:** comment.md, the issue thread, and the repo rules.

**What good looks like:** The comment talks about the actual issue, follows the repo rules, and includes anything the repo requires such as AI-use disclosure.