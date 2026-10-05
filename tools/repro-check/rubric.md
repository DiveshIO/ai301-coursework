# Rubric: is this reproduction package ready to post?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here. It ships empty on purpose: the judgment is your
work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the claim comment, the repro report's environment
     record, the artifacts read against the issue's description, the
     repo-facts block) or a location from your
     references/evidence-guide.md. "The report" is not a source; "the
     output excerpt read against the error the issue describes" is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (does
     the artifact show the issue's behavior?), never the write-up's
     shape (how many steps it has, how long it is, whether it uses a
     template's headings). Structure-shaped checks are what make
     graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad packages posted. The lecture named the
proof families: the environment is recorded, the steps are complete
and followable, the behavior shown matches the issue (not an adjacent
one), the outcome is stated honestly (an evidenced cannot-reproduce is
a pass, a confident wrong-target is not), and the words respect the
repo's conventions. A rubric that ignores a family will fail eval
packages designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| environment | Environment information in the repro report and repo-facts block | The environment records the repo version, runtime, dependencies, and other details needed to compare the reproduction with the issue. If the environment is different from the issue target, the difference is stated. | required |
| steps | Steps in the reproduction report | The steps include the starting state and the commands or actions used to test the issue. They must be enough for another person to repeat the same test without guessing missing setup. | required |
| behavior | Output, logs, screenshots, or other artifacts read against the behavior described in the GitHub issue | The evidence shows the behavior described by the issue, or shows that the reported behavior did not occur in the tested environment. Evidence of only a related or different behavior does not pass. | required |
| outcome | The reported result and the supporting evidence | The report states whether the issue was reproduced or could not be reproduced, and every claim about the result is supported by the evidence shown. | required |
| conventions | Claim and reproduction comments, plus the repo's contribution and communication rules | The comments follow the repo's stated rules and include any required information or AI-use disclosure. | required |
| evidence | Screenshots, output, logs, or other proof in the reproduction package | The evidence supports the reported outcome and can be connected to the issue and the steps that produced it. | required |

## Verdict rule
Accept if every required check passes.

Reject if any required check fails.

If any required check is unclear, treat it as fail.

Preferred checks do not change the verdict.

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict;
unclear counts as fail." -->
