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
| maintainer_activity | Last 5 default-branch commit dates in repo-facts | The newest commit is no more than 30 days old | required |
| repo_usage | Repo-facts commit list and author info from the past 90 days | At least 3 commits in the past 90 days from at least 2 different authors | required |
| issue_open | Issue header: state and labels | The issue is open and does not have `wontfix`, `duplicate`, `invalid`, `blocked`, or `on hold` | required |
| newcomer_scope | Issue body and maintainer comments about the fix | PASS unless the issue clearly asks for a redesign, rewrite, large refactor, migration, new subsystem, new integration, or architecture change. It also fails if it lists 4 or more files, modules, or components to change, has 4 or more separate tasks, or a maintainer says it is large or complex. Naming files as context, having no file list, or having a small checklist does not fail this check. A small bug fix, docs change, test, or feature passes. UNCLEAR only if the issue body is empty | required |
| not_assigned | Issue header: assignees | There are no assignees | required |
| no_linked_pr | Issue body, comments, and linked PR information | There is no open or merged PR linked to or described as fixing the issue | required |
| no_active_claim_comment | Comment thread | Nobody said they are working on or taking the issue within the last 14 days, unless they later withdrew. Claims older than 14 days with no follow-up count as abandoned | required |
| policy_compliance | Issue, comments, README, CONTRIBUTING, and policy text in repo-facts | PASS unless the project does not allow this type of contribution, the issue is maintainers-only or internal, the issue says not to open a PR, or the task asks for something that breaks security, licensing, or other project rules | required |
| maintainer_response | Issue body and comments | A maintainer commented on the issue within the past 90 days | preferred |
| issue_evidence | Issue body and comments | The issue has at least one useful detail such as reproduction steps, an error message, a file or function name, or acceptance criteria | preferred |
| maintainer_welcomes | Issue labels and comments | The issue has a label like `good first issue` or `help wanted`, or a maintainer says they will accept a PR | preferred |
| contributing_docs | Repo-facts file list, README, or CONTRIBUTING | There is a CONTRIBUTING file or README section explaining setup or how to submit changes | preferred |
| has_tests | Repo-facts file list | A test directory or test config exists | preferred |
| issue_recency | Issue header: created date | The issue was opened within the past 12 months | preferred |

## Verdict rule
- Accept if every required check passes
- Reject if any required check fails
- `unclear` on a required check counts as fail
- `unclear` on a preferred check counts as fail for ranking only
- Preferred checks never change accept or reject
- Accepted issues can be ranked by how many preferred checks pass
- If two issues have the same number of preferred checks, use the more recent maintainer comment as the tie breaker

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict, they
rank accepted issues; unclear counts as fail." -->
