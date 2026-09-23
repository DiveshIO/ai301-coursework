# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the
wrong label is not graded.

---

## Selected issue

**Issue link**

[The individual Path Review issue page. A link to the repository or the issue list
does not satisfy this field.]
https://github.com/codepath/pathreview-ai301-fa26-s1/issues/61 Final

`claude "issue-select: grade these candidate first issues: https://github.com/codepath/pathreview-ai301-fa26-s1/issues/61 https://github.com/codepath/pathreview-ai301-fa26-s1/issues/54 https://github.com/codepath/pathreview-ai301-fa26-s1/issues/58"`

**Verdict output**

[Your skill's live-mode output for this issue, pasted verbatim and ending with the
fenced JSON verdict block. A summary does not satisfy this field.]
Grading summary

Scope check: All three issues are in codepath/pathreview-ai301-fa26-s1, the scoped repo — all admissible candidates.

Repo-level facts (shared by all three): newest commit 2026-09-16 (7 days old) → maintainer_activity pass. 3+ authors (Aburke225, ascherj, margaretfero-codepath) with multiple commits in the last 90 days → repo_usage pass. docs/CONTRIBUTING.md exists with setup/PR instructions, no AI-contribution ban (this is the course's own AI-assisted workflow) → contributing_docs and policy_compliance pass. tests/ directory exists → has_tests pass.

┌─────────────────────────┬─────────────────────────────────┬──────────────────────────────┬─────────────────────────────────────────────┐
│          Check          │    #61 (health check text())    │  #54 (resume section regex)  │          #58 (bias detector regex)          │
├─────────────────────────┼─────────────────────────────────┼──────────────────────────────┼─────────────────────────────────────────────┤
│ issue_open              │ pass (open, no blocking labels) │ pass                         │ pass                                        │
├─────────────────────────┼─────────────────────────────────┼──────────────────────────────┼─────────────────────────────────────────────┤
│ not_assigned            │ pass (no assignees)             │ pass                         │ pass                                        │
├─────────────────────────┼─────────────────────────────────┼──────────────────────────────┼─────────────────────────────────────────────┤
│ no_linked_pr            │ pass (no PR search hits)        │ pass                         │ pass                                        │
├─────────────────────────┼─────────────────────────────────┼──────────────────────────────┼─────────────────────────────────────────────┤
│ no_active_claim_comment │ pass (0 comments)               │ pass (0 comments)            │ pass (0 comments)                           │
├─────────────────────────┼─────────────────────────────────┼──────────────────────────────┼─────────────────────────────────────────────┤
│ newcomer_scope          │ pass (1 file, 1-line fix)       │ pass (1 function, 1 file)    │ pass (1 file, general pattern-widening)     │
├─────────────────────────┼─────────────────────────────────┼──────────────────────────────┼─────────────────────────────────────────────┤
│ maintainer_welcomes     │ pass (good first issue)         │ pass (good first issue)      │ fail (no such label, no maintainer comment) │
├─────────────────────────┼─────────────────────────────────┼──────────────────────────────┼─────────────────────────────────────────────┤
│ maintainer_response     │ fail (no comments)              │ fail                         │ fail                                        │
├─────────────────────────┼─────────────────────────────────┼──────────────────────────────┼─────────────────────────────────────────────┤
│ issue_evidence          │ pass (repro + error text)       │ pass (repro + failing tests) │ pass (repro + failing tests)                │
├─────────────────────────┼─────────────────────────────────┼──────────────────────────────┼─────────────────────────────────────────────┤
│ issue_recency           │ pass (opened 2026-09-10)        │ pass                         │ pass                                        │
└─────────────────────────┴─────────────────────────────────┴──────────────────────────────┴─────────────────────────────────────────────┘

Verdicts: all three accept — every required check passes for each.

Ranking: #61 and #54 tie at 5/6 preferred passes; #58 trails at 4/6 (missing maintainer_welcomes). The rubric's tiebreaker (most recent maintainer comment) doesn't resolve #61 vs. #54 since neither has any comments — I broke the tie using your fit profile: #61 is the tightest possible scope (one raw-SQL-string call site, wrap in sqlalchemy.text()), the cleanest "read one function, fix one line" first PR. #54 is a close second — also single-file/single-function, slightly more regex reasoning. #58 is viable but weaker: it lacks the good first issue signal and is the vaguest of the three about how many phrasing patterns actually need to be added.

[
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/61",
    "checks": [
      {"name": "maintainer_activity", "grade": "pass", "evidence": "newest default-branch commit 2026-09-16, 7 days before capture"},
      {"name": "repo_usage", "grade": "pass", "evidence": "commits from Aburke225, ascherj, margaretfero-codepath within past 90 days"},
      {"name": "issue_open", "grade": "pass", "evidence": "state: OPEN, labels: bug, good first issue, api, tier-1"},
      {"name": "newcomer_scope", "grade": "pass", "evidence": "single file api/routes/health.py, one-line fix wrapping SQL in text()"},
      {"name": "not_assigned", "grade": "pass", "evidence": "assignees: []"},
      {"name": "no_linked_pr", "grade": "pass", "evidence": "gh pr list search for '61' returned no results"},
      {"name": "no_active_claim_comment", "grade": "pass", "evidence": "comments: []"},
      {"name": "policy_compliance", "grade": "pass", "evidence": "CONTRIBUTING.md has no AI-contribution restriction; course workflow is AI-assisted"},
      {"name": "maintainer_response", "grade": "fail", "evidence": "comments: [] — no maintainer reply"},
      {"name": "issue_evidence", "grade": "pass", "evidence": "gives exact error text: ArgumentError: Textual SQL expression 'SELECT 1'..."},
      {"name": "maintainer_welcomes", "grade": "pass", "evidence": "label 'good first issue' present"},
      {"name": "contributing_docs", "grade": "pass", "evidence": "docs/CONTRIBUTING.md exists with setup/PR steps"},
      {"name": "has_tests", "grade": "pass", "evidence": "tests/ directory exists in repo tree"},
      {"name": "issue_recency", "grade": "pass", "evidence": "createdAt 2026-09-10, within 12 months"}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/54",
    "checks": [
      {"name": "maintainer_activity", "grade": "pass", "evidence": "newest default-branch commit 2026-09-16, 7 days before capture"},
      {"name": "repo_usage", "grade": "pass", "evidence": "commits from Aburke225, ascherj, margaretfero-codepath within past 90 days"},
      {"name": "issue_open", "grade": "pass", "evidence": "state: OPEN, labels: bug, good first issue, ingestion, tier-1"},
      {"name": "newcomer_scope", "grade": "pass", "evidence": "single function _detect_sections() in one file resume_parser.py"},
      {"name": "not_assigned", "grade": "pass", "evidence": "assignees: []"},
      {"name": "no_linked_pr", "grade": "pass", "evidence": "gh pr list search for '54' returned no results"},
      {"name": "no_active_claim_comment", "grade": "pass", "evidence": "comments: []"},
      {"name": "policy_compliance", "grade": "pass", "evidence": "CONTRIBUTING.md has no AI-contribution restriction; course workflow is AI-assisted"},
      {"name": "maintainer_response", "grade": "fail", "evidence": "comments: [] — no maintainer reply"},
      {"name": "issue_evidence", "grade": "pass", "evidence": "gives repro code snippet and names 3 failing tests"},
      {"name": "maintainer_welcomes", "grade": "pass", "evidence": "label 'good first issue' present"},
      {"name": "contributing_docs", "grade": "pass", "evidence": "docs/CONTRIBUTING.md exists with setup/PR steps"},
      {"name": "has_tests", "grade": "pass", "evidence": "tests/ directory exists in repo tree"},
      {"name": "issue_recency", "grade": "pass", "evidence": "createdAt 2026-09-10, within 12 months"}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/58",
    "checks": [
      {"name": "maintainer_activity", "grade": "pass", "evidence": "newest default-branch commit 2026-09-16, 7 days before capture"},
      {"name": "repo_usage", "grade": "pass", "evidence": "commits from Aburke225, ascherj, margaretfero-codepath within past 90 days"},
      {"name": "issue_open", "grade": "pass", "evidence": "state: OPEN, labels: bug, safety, tier-1"},
      {"name": "newcomer_scope", "grade": "pass", "evidence": "single file bias_detector.py, no 4+ file/task list, no maintainer complexity flag"},
      {"name": "not_assigned", "grade": "pass", "evidence": "assignees: []"},
      {"name": "no_linked_pr", "grade": "pass", "evidence": "gh pr list search for '58' returned no results"},
      {"name": "no_active_claim_comment", "grade": "pass", "evidence": "comments: []"},
      {"name": "policy_compliance", "grade": "pass", "evidence": "CONTRIBUTING.md has no AI-contribution restriction; course workflow is AI-assisted"},
      {"name": "maintainer_response", "grade": "fail", "evidence": "comments: [] — no maintainer reply"},
      {"name": "issue_evidence", "grade": "pass", "evidence": "gives repro code snippet and names 9 failing tests"},
      {"name": "maintainer_welcomes", "grade": "fail", "evidence": "no 'good first issue'/'help wanted' label, no maintainer comment"},
      {"name": "contributing_docs", "grade": "pass", "evidence": "docs/CONTRIBUTING.md exists with setup/PR steps"},
      {"name": "has_tests", "grade": "pass", "evidence": "tests/ directory exists in repo tree"},
      {"name": "issue_recency", "grade": "pass", "evidence": "createdAt 2026-09-10, within 12 months"}
    ],
    "verdict": "accept"
  }
]


**The verdict must record `accept` for this issue.** Choose an issue your own skill
accepts. If your skill rejects every candidate you try, that is a signal about your
rubric rather than about the issues: revise it and re-run — retries are unlimited and a
partial re-run costs about $0.20 — or run the skill on different candidates. Output
recording `reject` for the issue you chose earns no credit for this field.

```
paste the output here, including the closing JSON block
```

---

## Eval iterations

Quote source text directly in each field below. Paraphrase does not satisfy them.

**Run history**

[The agreement score of each run you did, in order. A single run is a complete answer if
only one run occurred. **The last score in your list must match the agreement line in the
`eval-run.txt` you committed** — that file is the record of your final run.]
1. Run 1 (Full) 14/20
2. Run 2 (Full) 14/20
3. Change the newcomer_scope
4. Run 4 (cheap, 6 issue): unable to fix all the issues.
5. Final run: 14/20

**Issue analysis**

[One scored issue, identified by id (`issue-01` through `issue-20`; the `calib-`
issues are not scored). State your rubric's decision, the gold label, and the
reasoning that produced your rubric's result.]

For issue-01, my rubic result was reject, but the goal label was accept. The rubric rejected it because the newcomer_scope check failed. The issue also failed some prefrred checks, including maintainer_response, maintaier_welocomes, and has_tests, but those preferred checks did not cause the rjection. This shows my rubic was way too strict. and only provide unclear if only the issues is empty and way too unclear.

**Check rationale**

[One check from the `rubric.md` uploaded to `tools/issue-select/`, quoted as it is
currently written, with the reasoning behind its current form.]

“PASS unless the issue clearly asks for a redesign, rewrite, large refactor, migration, new subsystem, new integration, or architecture change. It also fails if it lists 4 or more files, modules, or components to change, has 4 or more separate tasks, or a maintainer says it is large or complex. Naming files as context, having no file list, or having a small checklist does not fail this check. A small bug fix, docs change, test, or feature passes. UNCLEAR only if the issue body is empty”

The design was made to pass unless the issues required a new bigger changes. it also if the mainters says it would be large or complex or when it fails a basic checklists. 

**Trade-offs**

[What the quoted check gives up. Any one of these is a complete answer: an issue whose
result it changes, a canary you re-ran with `--only`, a case you accept it will miss, or a
stated reason nothing changed elsewhere. "Nothing changed, and here is how I know" earns
the point in full when the reason follows.]

The trade-off is that the checklist may allow some issues that could be way too hard, or when the issue's difficulty was not listed, if they are not done, it can allow them, but it is worth looking at previous sources for difficulty instead of asking the program to think, which can provide false positives.

---

## Selection rationale

Graded on whether all three are answered, in your own words. Not on how good the
reasoning is, and not on length — a short honest answer to each earns the full marks.
This is also the basis for the claim comment you write in Unit 2.

**Selection rationale**

[Answer all three:

1. The issue's fit to your interests and to the time available.

Issue #61 fits my interests because it involves Python and a small code change related to my programming skills. The scope also looks small enough to finish with the time I have.

2. What the verdict identified correctly, and what you weighed that the rubric could
   not.
The verdict correctly identified that the issue has a clear and small scope for a first contribution. I also considered whether the issue matches my skills and whether I have enough time to work on it.

3. The anticipated difficulty in claiming it.]
I think it should be easy to claim if nobody else has claimed it. The main difficulty would be someone else claiming it first.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
