# Rubric: is this a good first issue?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever checks
you define here. It ships empty on purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where. Name the source
     (repo-facts block, issue body, comment thread, or the locations in
     references/evidence-guide.md). "The repo" is not a source; "the last
     5 default-branch commit dates" is.
   - Pass condition: a condition someone else could apply and get your
     answer. Prefer thresholds with numbers ("a maintainer commented
     within 30 days") over adjectives ("maintainer is responsive").
   - Weight: `required` (a fail here rejects the issue) or `preferred`
     (never changes the verdict; a nice-to-have that helps rank the
     issues you accept).

2. A verdict rule below the table: how the check grades combine into
   accept or reject, including how `unclear` is treated. The verdict
   space is binary. If you write no rule for `unclear`, the skill treats
   it as fail.

Cover what actually kills first contributions. The lecture named four
families: the maintainer is alive, the repo is in use, the scope fits a
newcomer, and nobody else is already on it. A rubric that ignores a family
will fail eval issues designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| maintainer_activity | The last 5 default-branch commit dates in repo-facts | The newest of the last 5 commits is no more than 30 days old | required |
| repo_usage | Repo-facts: commit list and contributor/author info for the past 90 days | At least 3 commits on the default branch in the past 90 days, from at least 2 distinct authors | required |
| issue_open | Issue header: state and labels | The issue is open and has none of the labels `wontfix`, `duplicate`, `invalid`, `blocked`, or `on hold` | required |
| newcomer_scope | Issue body and any maintainer comment that sketches the fix. Grade only from the text; do not estimate effort or file counts yourself | PASS unless the text explicitly contains a red flag: (a) it asks for a redesign, rewrite, whole-module refactor, migration, new subsystem, new integration, or architecture change; (b) it lists 4 or more separate files, modules, or components to change; (c) it is an epic or tracking issue with 4 or more separate tasks; (d) a maintainer calls it large or complex, or says it needs a design decision or RFC before work starts. These are NOT red flags: naming several files as context, a checklist of steps inside one function or feature, a maintainer suggesting an approach, or a missing file list. A single bug fix, docs change, test addition, or small feature with a stated expected behavior passes. Quote the red-flag sentence as evidence when failing. UNCLEAR only if the issue body is empty | required |
| not_assigned | Issue header: assignees | The assignee list is empty | required |
| no_linked_pr | Issue body, comment thread, and any linked-PR or cross-reference events | No open or merged PR is linked to or described as fixing this issue | required |
| no_active_claim_comment | Comment thread | No comment saying "I'll take this", "working on it", or similar within the last 14 days, unless the commenter later withdrew. A claim older than 14 days with no follow-up counts as abandoned | required |
| policy_compliance | Issue body, comment thread, and any README, CONTRIBUTING, or policy text included in repo-facts | PASS unless the text explicitly shows one of: (a) the project's own policy forbids this kind of contribution (for example a ban on AI/LLM-generated code, or a rule that PRs are accepted only after a maintainer approves or assigns the issue, with no such approval shown); (b) the issue says it is maintainers-only, internal, not open to outside contributors, or "do not open a PR"; (c) the task asks the contributor to bypass security controls, copy code under an incompatible license, scrape restricted data, spam, or deceive. Quote the policy or issue text as evidence | required |
| maintainer_response | Issue body and comment thread | A maintainer (owner, member, or collaborator) commented on this issue within the past 90 days. If there is no maintainer comment, this check fails | preferred |
| issue_evidence | Issue body and comment thread | The issue gives at least one concrete pointer: reproduction steps, an error message, a named file or function, or explicit acceptance criteria | preferred |
| maintainer_welcomes | Issue labels and comment thread | The issue has a label such as `good first issue` or `help wanted`, or a maintainer wrote that they would accept a PR | preferred |
| contributing_docs | Repo-facts: file list or README/CONTRIBUTING mentions | A `CONTRIBUTING` file or a README section explains setup or how to submit a change | preferred |
| has_tests | Repo-facts: file list | A test directory or test config exists, so a newcomer can verify their change | preferred |
| issue_recency | Issue header: created date | The issue was opened within the past 12 months | preferred |

## Verdict rule

- Accept if every `required` check passes. Otherwise reject.
- `unclear` on a `required` check counts as `fail`.
- `unclear` on a `preferred` check counts as `fail` for ranking only.
- Preferred checks never change the verdict.
- Rank accepted issues by the number of preferred checks that pass, highest first. Break ties by the more recent maintainer comment.

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict, they
rank accepted issues; unclear counts as fail." -->
