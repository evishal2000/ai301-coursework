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
| maintainer-active | Repo-facts: archived status, last five default-branch commits; supplied maintainer comments and PR activity. | Not archived, with at least one human change, merge, or substantive maintainer response within 90 days before capture. Bot-only activity is insufficient. | required |
| repo-in-use | Repo-facts: release dates and commit history; issue thread: dated usage reports. | A release within 365 days, human-authored or reviewed default-branch change within 90 days, or concrete current-version usage report within 90 days. Releases are not mandatory; stars alone are insufficient. | required |
| scope-fits | Issue body and full comment thread: requested outcome, diagnosis, affected areas, unresolved design decisions, and the dated history of claims, attempts, and closed PRs. | One bounded bug, docs task, performance fix, or specified feature. Clear behavior or a maintainer diagnosis with named causes is sufficient; formal reproductions and numeric benchmarks are optional. One user-visible symptom whose diagnosis lists several causes, sub-fixes, or optional suggestions is still one bounded change, not umbrella work. Fail only for: a deliverable that is a list of independent tasks or linked issues; a codebase-wide sweep with no completion condition; an unresolved product, API, or UX decision; or a thread showing repeated stalling, meaning three or more distinct contributors claimed or attempted it without finishing, or two or more PRs closed unmerged, spanning a year or more with the issue still open. Age alone does not fail. | required |
| unclaimed | Repo-facts: assignees and PRs; comments: claims, progress, withdrawals, and maintainer invitations. | No current assignee, open competing PR, or claim made/reaffirmed within 30 days. Ignore older informal claims without recent progress. Later maintainer invitations override earlier informal claims, not current assignments or open PRs. Unknown referenced-PR status is unclear; already completed work fails. | required |
| policy-compatible | Supplied contribution-policy summary, CONTRIBUTING.md, AI_USAGE_POLICY.md, and AGENTS.md. | The planned AI-assisted workflow is allowed. Distinguish permitted assistance from prohibited full generation. Explicitly reported absence of a tooling policy passes; missing or ambiguous evidence is unclear. | required |
| maintainer-responsive | Repo-facts response sample and supplied issue comments, including author roles and dates. | At least one non-maintainer's issue received a substantive maintainer response within 30 days. Exclude bots and self-replies. | preferred |

## Verdict rule

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict, they
rank accepted issues; unclear counts as fail." -->

Accept only if every required check passes. Required fail or unclear
means reject. Preferred checks only rank accepted issues and never
change the verdict.

Use the capture date and supplied bundle only. Missing evidence is
unclear. Cite the evidence or missing information behind each failed
or unclear check; do not use gold labels as evidence.
