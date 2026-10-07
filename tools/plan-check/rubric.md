# Rubric: is this plan ready to post and build from?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here (via your procedure.md). It ships empty on
purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the plan's scope statement, the test plan read against
     the repro evidence's steps, the plan comment read against the
     thread highlights, the repo-facts block) or a location from your
     references/evidence-guide.md. "The plan" is not a source; "the
     plan's stated cause read against what the repro evidence shows"
     is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (is
     this one bounded change? could a stranger start executing it?),
     never the write-up's shape (how many sections it has, how long it
     is, whether it uses headings). Structure-shaped checks are what
     make graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad plans posted. The lecture named the
failure families: the diagnosis ignores or contradicts the reproduced
evidence, the change is unbounded (scope creep), the plan targets the
symptom while the evidence points at the cause, a stranger could not
start executing it, the test plan proves nothing observable, the
unknowns are dressed up as certainty, and the comment ignores what the
thread or the repo's stated conventions ask. A rubric that ignores a
family will fail eval packages designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| diagnosis | The diagnosis in the plan and the reproduction evidence | The diagnosis matches what the reproduction evidence shows and does not say something happened when the evidence does not show it. | required |
| scope | The scope, files, and things the plan says it will change | The plan only changes what is needed for the issue and does not add unrelated work. | required |
| cause | The diagnosis, reproduction evidence, and planned fix | The planned fix works on the cause shown by the evidence and is not only hiding the problem. If the cause is not fully known, the plan says what needs to be checked. | required |
| execution | The files, approach, and steps in the plan | Someone else can start working from the plan without needing to ask what they should do first. | required |
| test | The test plan and the reproduction steps and results | The plan tests the real code and has an expected result that can show if the fix worked. | required |
| honesty | The diagnosis, risks, unknowns, and Deviations section | The plan does not claim something is known when it is not. Unknowns are listed, and changes from the plan are put under Deviations. | required |
| conventions | The plan comment, issue thread, and repo rules | The plan comment follows the repo rules, uses information from the issue thread when needed, and includes any required disclosure. | required |

## Verdict rule

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict;
unclear counts as fail." -->

- Accept if every required check passes. 
- Reject if any required check fails. 
- If a check is unclear, treat it as a fail.
