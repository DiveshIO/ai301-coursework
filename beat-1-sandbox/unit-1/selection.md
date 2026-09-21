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

**Verdict output**

[Your skill's live-mode output for this issue, pasted verbatim and ending with the
fenced JSON verdict block. A summary does not satisfy this field.]

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
5. Final fun: 14/20

**Issue analysis**

[One scored issue, identified by id (`issue-01` through `issue-20`; the `calib-`
issues are not scored). State your rubric's decision, the gold label, and the
reasoning that produced your rubric's result.]
I fixed it by making newcomer_scope pass by default and fail only when the text contains a named red flag (redesign or rewrite, 4+ files, an epic with  + tasks, or a maintainer saying it is large). I also listed what does not count as a red flag, such as naming files as context or having no file list at all. After that change, issue-01 

**Check rationale**

[One check from the `rubric.md` uploaded to `tools/issue-select/`, quoted as it is
currently written, with the reasoning behind its current form.]
I wrote it to this way to prevent the rubric from failing. 

**Trade-offs**

[What the quoted check gives up. Any one of these is a complete answer: an issue whose
result it changes, a canary you re-ran with `--only`, a case you accept it will miss, or a
stated reason nothing changed elsewhere. "Nothing changed, and here is how I know" earns
the point in full when the reason follows.]
I had issue with making the newcommer scope and pass-by-default where the issues was it had fales reject where i had to make sure it has false reject to make sure it passes.

---

## Selection rationale

Graded on whether all three are answered, in your own words. Not on how good the
reasoning is, and not on length — a short honest answer to each earns the full marks.
This is also the basis for the claim comment you write in Unit 2.

**Selection rationale**

[Answer all three:

1. The issue's fit to your interests and to the time available.
The issue fits my interest because it provides a change to work on something related to my skills. The scope works with the time.

2. What the verdict identified correctly, and what you weighed that the rubric could
   not.
The verdict correctly identify that issue has a clear scope for contribution
3. The anticipated difficulty in claiming it.]
I think it should be easy if noone claimed it.
---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
