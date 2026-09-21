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

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/33

**Verdict output**

**The verdict must record `accept` for this issue.** Choose an issue your own skill
accepts. If your skill rejects every candidate you try, that is a signal about your
rubric rather than about the issues: revise it and re-run — retries are unlimited and a
partial re-run costs about $0.20 — or run the skill on different candidates. Output
recording `reject` for the issue you chose earns no credit for this field.

```
Every required check passes → accept. Preferred check unclear; does not change the verdict. Fit ranking not applicable (single candidate; and scope.md's fit profile is still the placeholder "(Write a few sentences here.)", so it wouldn't discriminate anyway).

{
  "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/33",
  "checks": [
    {"name": "maintainer-active", "grade": "pass", "evidence": "Not archived; human commit 2f4e82f5 by staff Aburke225 on 2026-09-16 (4 days before capture), plus additional human commits ddb377d2 and f011a77e same day."},
    {"name": "repo-in-use", "grade": "pass", "evidence": "Human-authored default-branch commits by Aburke225 on 2026-08-24 and 2026-09-16 fall within 90 days; repo description confirms current course use ('AI301 Fall 2026 Section 3 student copy')."},
    {"name": "scope-fits", "grade": "pass", "evidence": "Bounded specified feature with prescribed fix ('Add a per-profile lock to serialize concurrent reviews'), named files api/routes/reviews.py and core/services/review_service.py, and 6-9h estimate; no umbrella, no unresolved design, no stalling (0 comments, 0 linked PRs)."},
    {"name": "unclaimed", "grade": "pass", "evidence": "Assignees empty; 0 issue comments; GitHub PR search returned 0 PRs referencing #33; no informal claim to override."},
    {"name": "policy-compatible", "grade": "pass", "evidence": "docs/CONTRIBUTING.md contains no AI restrictions and no AGENTS.md/AI_USAGE_POLICY.md/AI_POLICY.md exists at repo root (all HTTP 404); explicit absence of a tooling policy passes per the evidence guide."},
    {"name": "maintainer-responsive", "grade": "unclear", "evidence": "Issue has 0 comments and was opened by staff (Aburke225, COLLABORATOR), so no non-maintainer thread exists on this issue to measure response latency; preferred check does not change the verdict."}
  ],
  "verdict": "accept"
}
```

---

## Eval iterations

Quote source text directly in each field below. Paraphrase does not satisfy them.

**Run history**

I ran the full eval three times. In order:

1. `agreement: 16/20 scored items  (bar: 18/20: below the bar)`
2. `agreement: 18/20 scored items  (bar: 18/20: PASS)`
3. `agreement: 20/20 scored items  (bar: 18/20: PASS)`

The third score matches the agreement line in the committed `eval-run.txt`.

**Issue analysis**

My rubric graded **issue-19** as `reject`; the gold label was `accept`. The second
run reported it as a disagreement:

```
issue-19  accept  reject   NO     failed: scope-fits
```

The failing check was `scope-fits`. The gold explanation was:

> maintainer-diagnosed performance bug with named causes, unclaimed

My reasoning had been that an issue naming several causes was umbrella work.
Comparing that against the gold explanation, I decided the cause count was the
wrong signal: one user-visible symptom whose diagnosis lists several causes or
sub-fixes is still one bounded change. I also decided that a maintainer diagnosis
is enough to bound a performance fix, without formal reproduction steps or a
numeric benchmark. I wrote both rules into the `scope-fits` pass condition, and
the final run agreed:

```
issue-19  accept  accept   yes
```

**Check rationale**

My final scope-fits check is:

| Check      | Evidence                                                                                                                                                                  | Pass condition                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | Weight   |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| scope-fits | Issue body and full comment thread: requested outcome, diagnosis, affected areas, unresolved design decisions, and the dated history of claims, attempts, and closed PRs. | One bounded bug, docs task, performance fix, or specified feature. Clear behavior or a maintainer diagnosis with named causes is sufficient; formal reproductions and numeric benchmarks are optional. One user-visible symptom whose diagnosis lists several causes, sub-fixes, or optional suggestions is still one bounded change, not umbrella work. Fail only for: a deliverable that is a list of independent tasks or linked issues; a codebase-wide sweep with no completion condition; an unresolved product, API, or UX decision; or a thread showing repeated stalling, meaning three or more distinct contributors claimed or attempted it without finishing, or two or more PRs closed unmerged, spanning a year or more with the issue still open. Age alone does not fail. | required |

The check is written this way to separate a focused problem that happens to
take several implementation steps from a collection of independent tasks —
the distinction that issue-19 forced me to make explicit. It reads the whole
comment thread, not just the body, because a short description can hide an
unresolved design decision or a history of stalled attempts. I gave the
failure cases numeric thresholds (three or more contributors, two or more
unmerged PRs, a year or more open) so the judgment is repeatable by someone
else, but those numbers are heuristics for difficulty, not evidence of it.

**Trade-offs**

The check states:

> formal reproductions and numeric benchmarks are optional.

This admits useful performance fixes, but it may also accept work
whose investigation takes longer than expected.

It also rejects a history containing:

> two or more PRs closed unmerged, spanning a year or more with the issue still open.

That can exclude a solvable issue when earlier contributors stopped
for personal reasons rather than technical difficulty. I accept that
risk to favor more predictable first contributions.

Between the reported 18/20 and 20/20 runs, issue-15 changed from accept
to reject and issue-19 changed from reject to accept. The other 18
verdicts stayed the same. Because I used feedback from these examples
to refine the rubric, the final score does not establish performance
on unseen issues.

---

## Selection rationale

Graded on whether all three are answered, in your own words. Not on how good the
reasoning is, and not on length — a short honest answer to each earns the full marks.
This is also the basis for the claim comment you write in Unit 2.

**Selection rationale**

[Answer all three:

1. The issue's fit to your interests and to the time available.
   Issue #33 fits my interest in backend development and concurrency.
   The proposed per-profile lock gives me a focused opportunity to
   work on concurrent requests in Python. The reported 6–9-hour
   estimate is useful for planning, although I need to allow
   additional time for setup, reproduction, and testing.

2. What the verdict identified correctly, and what you weighed that the rubric could
   not.
   The verdict identified a bounded change, named implementation
   files, recent repository activity, and no ownership blockers at
   the time of the run. I also considered the learning opportunity:
   understanding how the lock is acquired and released and how to
   test concurrent requests. The rubric does not establish my
   familiarity with this codebase or guarantee the time estimate.
   Maintainer responsiveness remained unclear, which I would keep
   in mind when planning for questions.

3. The anticipated difficulty in claiming it.
   I anticipate little difficulty claiming it. The live output
   reported no assignee, comments, or linked PRs, and the Path Review
   house rules allow shared issues even if classmates later claim
   it. I will wait until Unit 2 to write and post the claim comment.
   ]

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
