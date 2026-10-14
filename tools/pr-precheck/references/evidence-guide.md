Evidence guide: where evidence lives in a PR package

Plan fidelity (harness category: silent-drift)

Where it lives

* Eval mode: Read the plan-context block’s scope pair, planned file list, exclusions, intended behavior, and deviation notes. Compare these with the candidate PR’s diff and commit list. Check the PR description against the actual diff, and use the issue context to verify that the change addresses the reported problem.
* Live mode: Read plan.md, including ## Deviations, before comparing it with git diff main...HEAD, the changed-file list, and the branch commits. Read the title and description in pr_draft.md and compare their claims with the actual implementation. Use the issue thread to confirm the intended behavior and any maintainer constraints.

What good looks like

Every changed file and substantive change falls within the plan’s stated scope or is accounted for by an explicit, supported deviation. Planned changes are implemented or their omission is explained, and the PR title and description accurately describe what the diff delivers without claiming missing work or hiding material changes.

Silent drift occurs when the implementation adds unplanned work, omits planned work without explanation, or changes the intended behavior without a justified deviation. A deviation note makes a difference visible, but does not automatically make unrelated or unjustified work acceptable.

Test evidence (harness category: not-tested)

Where it lives

* Eval mode: Read the plan-context block’s test plan and reproduction steps alongside the candidate PR’s test-evidence section. Inspect the before-and-after commands, outputs, expected behavior, and reported results for the relevant checks. Use the repo-facts block for required project checks when supplied.
* Live mode: Read the test plan and reproduction steps in plan.md, then inspect test_evidence.md for actual commands and captured output. Compare the before-and-after reproduction results and inspect results for make test-unit, make test-integration, make lint, make typecheck, and other checks required by the plan or repository guidance. Consult docs/CONTRIBUTING.md for additional testing requirements.

What good looks like

The evidence identifies the behavior being tested, shows a reproducible command or test, states the expected result, and provides actual output demonstrating whether that result occurred. Before-and-after evidence should establish the original failure and show that the changed code produces the expected behavior; the relevant repository checks should have visible, accurately reported outcomes.

A statement such as “all tests pass” is insufficient without supporting results. Distinguish passing checks from failing checks, checks that were not run, and checks blocked by environmental problems. A blocked or missing check must never be represented as a pass, and a passing unrelated test does not prove the reported defect is fixed.

Diff quality (harness category: unreviewable)

Where it lives

* Eval mode: Inspect the candidate PR’s unified diff and commit list. Use the plan-context block and the PR description for context, but judge the actual implementation from the changed code rather than from its summary.
* Live mode: Inspect git diff main...HEAD, including individual hunks, and review the branch’s commit list. Compare the changed files with the plan and inspect the surrounding code when needed to determine whether the fix is understandable and appropriately scoped.

What good looks like

The diff makes the intended fix identifiable, changes only code or tests needed for the issue, and gives reviewers enough context to understand the behavior change. Tests and supporting changes should serve the fix, and the commits should not conceal unrelated work.

Look for unrelated edits, unnecessary formatting churn, leftover debugging statements, dead code, commented-out implementations, accidental generated files, and unrelated configuration changes. Such signs warrant inspection rather than automatic rejection: grade their actual impact against the rubric. A small diff is not automatically good, and a larger diff is not automatically bad if its changes are justified and reviewable.

Standards and comms (harness category: standards-wall)

Where it lives

* Eval mode: Read the repo-facts block’s PR template requirements, contribution instructions, stated policies, AI-use disclosure requirements, and any explicit maintainer directions included in the package. Compare those requirements with the candidate PR’s title and description, including its testing, screenshots/demo, and reviewer-notes sections.
* Live mode: Inspect .github/PULL_REQUEST_TEMPLATE.md and docs/CONTRIBUTING.md, along with relevant maintainer instructions in the issue thread. Compare those requirements with the title and description in pr_draft.md and, when checking the submitted PR, the actual GitHub PR title and body. Check that required disclosures, including AI-use disclosure where required, are present.

What good looks like

The PR uses the required template, completes its required sections with specific and truthful information, follows repository contribution rules, includes required AI-use disclosure, and responds to explicit maintainer instructions. A section that does not apply should be marked appropriately, with a brief explanation where useful, rather than left blank or filled with unsupported claims.

Boilerplate that does not answer a required prompt, missing mandatory disclosure, or a visibly ignored repository rule is a standards failure when the applicable requirement is explicit. Do not invent requirements that are absent from the supplied repository guidance or package. Evaluate whether the stated requirements are met, not whether the PR description sounds polished.
