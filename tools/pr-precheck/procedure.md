Procedure: how this tool grades a PR package

Read order

1. Read scope.md to confirm which repository and PR package are in scope. If the package belongs to a different repository or cannot be identified, stop rather than grading the wrong change.
2. Read the issue thread and record the reported problem, reproduction steps, relevant maintainer guidance, and any constraints or conventions established in the discussion.
3. Read plan.md before examining the diff. Record the planned root cause, intended behavior, files to change, files or work explicitly excluded, test plan, known risks, unknowns, and deviations. This establishes the baseline for deciding whether implementation stayed within scope.
4. Read the repository’s docs/CONTRIBUTING.md and .github/PULL_REQUEST_TEMPLATE.md. Record required testing, contribution standards, required PR sections, and any disclosure requirements.
5. Read pr_draft.md and record the PR title, issue reference, summary, claimed changes, test claims, screenshots or demo information, and reviewer notes. Treat these as claims to verify, not proof that the work was completed.
6. Read test_evidence.md and record the reproduction commands and outputs, checks attempted, results, failures, and any limitations. Separate completed checks from planned or unavailable checks.
7. Examine git diff main...HEAD and its file list. Compare the actual changes against the plan’s scope and the PR description’s claims. The plan is the intended baseline, the diff is what was actually changed, the evidence shows what was tested, and the description explains what reviewers are being asked to review.
8. For evaluation mode, read the designated frozen package files and any package-specific instructions. For live mode, use the corresponding repository files, issue thread, branch diff, PR draft, and test evidence specified by the skill. Do not substitute a different package or invent missing evidence.

Evidence gathering

1. Issue and diagnosis: Use the issue thread and reproduction evidence to identify the reported behavior and expected outcome. Record which facts are demonstrated and which remain uncertain. Do not treat the issue’s suspected cause as proven unless the evidence supports it.
2. Plan and implementation scope: Make a list of every file the plan says will change, then compare it with the files in git diff main...HEAD. Record planned files that are missing, changed files not explained by the plan, and changes that appear unrelated. Inspect the actual diff for scope and behavior rather than relying on filenames alone.
3. Plan deviations: Compare the implementation with the plan’s approach, expected behavior, and exclusions. Record material differences and check whether they are explained under ## Deviations in plan.md. A justified change is not automatically a failure, but an unexplained material change must be assessed against the rubric.
4. PR description accuracy: Compare every substantive claim in pr_draft.md with the diff and test evidence. Verify the issue reference, summary, listed changes, and testing statements. Record claims that overstate what changed, describe work absent from the diff, or imply tests passed when the evidence shows otherwise.
5. Test-plan coverage: Compare each planned reproduction step and test with test_evidence.md. Record the command, observed result, and whether the result demonstrates the expected behavior. Identify missing tests, tests that were attempted but failed, and results that do not actually verify the relevant change.
6. Repository checks: Compare the evidence against the repository’s required checks and contribution guidance. Look for unit tests, integration tests, lint, type checking, and any other checks required by the project or plan. Distinguish a passing check from a failed check, a check not run, and a check blocked by an environmental issue. Never report a check as passing without supporting output.
7. Reproduction evidence: Compare the before and after reproduction commands and outputs. Confirm that the before result demonstrates the original problem and that the after result shows the expected behavior. If either side is absent or inconclusive, record that limitation rather than assuming the fix works.
8. Reviewability and standards: Check whether the diff is understandable and focused, whether the PR template’s required sections are filled out, and whether the description gives reviewers enough information to assess the change. Check required AI-use disclosure and other repository-specific requirements. Record missing sections or disclosures explicitly.
9. Evidence gaps: For every fact needed by a rubric check, record the exact file, diff hunk, issue-thread detail, command output, or PR section that supports the decision. If the package does not provide the evidence and the permitted sources do not resolve the gap, mark the check unclear rather than guessing.

Check execution

1. Execute the rubric checks in their listed order. For each check, identify its pass condition and compare it with the evidence already gathered.
2. Grade a check pass only when the available evidence satisfies its pass condition. Grade it fail when evidence demonstrates a violation or when a required condition is not met. Grade it unclear when the evidence is insufficient to determine whether the condition is met.
3. For scope-related checks, compare the plan’s stated scope and exclusions directly with the changed files and diff hunks. Do not reject a change solely because the implementation differs from the plan; determine whether the difference is material, necessary, and disclosed.
4. For testing checks, compare the test plan with actual commands and outputs. A test listed in the PR description is not proof it ran. A passing unrelated test does not prove the targeted behavior works. A failed or blocked command must be reported accurately, with the reason if known.
5. For claims checks, verify each claim in the PR description against the diff and test evidence. Do not infer that a feature, fix, or validation exists just because the description says it does.
6. For reviewability and standards checks, inspect the template, repository guidance, and reviewer-facing description. Missing required sections or disclosures are failures when the applicable rule explicitly requires them.
7. Reuse previously gathered evidence when it directly answers a check. Reopen a source only when the evidence is ambiguous, contradictory, or too incomplete to grade the check reliably.
8. When evidence is absent, first check the other permitted package sources for it. If it remains unavailable, mark the check unclear. Do not fill gaps with assumptions, invent command output, or silently treat an unrun check as successful.
9. Keep each grade tied to a specific piece of evidence and the rubric’s stated pass condition. Do not let a strong result on one check compensate for a failure on another required check.

Verdict assembly

1. Review the final grade for every required rubric check. Apply the rubric’s verdict rule exactly: accept only if every required check passes; reject if any required check fails or is unclear.
2. Do not average the grades or allow passing checks to cancel out a failed check. A required check graded unclear counts against acceptance.
3. If multiple required checks fail or remain unclear, select the first failing or unclear required check in the rubric’s listed order as the deciding check. This makes the verdict reproducible.
4. State the overall verdict as accept or reject, then provide a concise summary of the evidence supporting it.
5. Identify the deciding check by its exact rubric name. Quote the smallest relevant excerpt from the package or evidence, and identify its source. Explain briefly how that evidence satisfies or violates the check’s pass condition. If the check is unclear because evidence is missing, state exactly what evidence is unavailable instead of fabricating a quotation.
6. Mention other material failures or evidence gaps separately so the user can see what else needs attention, but do not change the deciding-check selection rule.
7. Keep the final output consistent with the skill’s required output format. Include the per-check grades and the required machine-readable JSON verdict, ensuring the JSON agrees with the written explanation.
8. Before finalizing, verify that the verdict follows from the recorded grades, the deciding check is the first failing or unclear required check, and every quoted claim is supported by the cited source.
