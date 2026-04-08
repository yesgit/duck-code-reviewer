---
name: code-reviewer
description: Review code snippets, files, diffs, commits, and PR/MR changes for correctness, security, maintainability, performance, testing, and best practices. Use when the user asks for code review, diff review, commit review, PR review, MR review, or security-focused review.
---

# Code Reviewer

## When to use

Use this skill when the user asks to:
- review a code snippet or file
- review a git diff or patch
- review a commit
- review a pull request or merge request
- focus on security, correctness, maintainability, performance, or testing risks

## Input classification

First classify the input before reviewing:
- code snippet or file content
- git diff or patch
- commit-level review
- pull request or merge request review
- security-focused review

Read [references/input-modes.md](references/input-modes.md), then load the matching reference:
- code snippet or file: [references/snippet-review.md](references/snippet-review.md)
- diff or patch: [references/diff-review.md](references/diff-review.md)
- commit: [references/commit-review.md](references/commit-review.md)
- PR or MR: [references/pr-mr-review.md](references/pr-mr-review.md)
- GitHub pull request with repo metadata or `gh` context: [references/github-pr-review.md](references/github-pr-review.md)
- GitLab merge request with repo metadata or `glab` context: [references/gitlab-mr-review.md](references/gitlab-mr-review.md)
- security-focused request: [references/security-review.md](references/security-review.md)

Always apply the baseline checklist in [references/review-checklist.md](references/review-checklist.md), the scoring rules in [references/scoring.md](references/scoring.md), and the output contract in [references/output-format.md](references/output-format.md).
Also follow [references/language-and-localization.md](references/language-and-localization.md) for output language and [references/cross-platform.md](references/cross-platform.md) for script portability expectations.

## Review workflow

1. Identify the review scope and the likely intent of the change.
2. Read the matching scenario reference for the input type.
3. Apply the baseline checklist and note missing context explicitly instead of guessing.
4. If the diff is noisy or too large, use:
   - `scripts/normalize_diff.py` to remove low-value noise
   - `scripts/split_diff.py` to split the diff into smaller chunks
5. Review each chunk for correctness, security, maintainability, performance, testing, and operational risk.
6. If multiple chunk-level reviews exist, use `scripts/summarize_findings.py` or equivalent reasoning to merge them.
7. Score the change using [references/scoring.md](references/scoring.md).
8. Format the answer exactly as defined in [references/output-format.md](references/output-format.md).
9. Match the user's language unless they request a different one explicitly.

## Review rules

- Prefer concrete findings over generic advice.
- Tie every substantial finding to a file, symbol, hunk, or behavior when possible.
- Distinguish confirmed bugs from uncertain risks.
- Call out missing tests when behavior changes are not covered.
- Avoid style-only nitpicks unless they affect readability, correctness, or maintainability.
- If the context is insufficient, say what is missing and how that limits confidence.
- For security-focused reviews, prioritize exploitable issues and unsafe defaults.

## Output requirements

Every review should include:
- a short summary of the change
- findings grouped by severity: high, medium, low, info
- for each finding: location, issue, impact, recommendation
- an overall risk assessment
- a score from 1 to 10
- the top 3 recommendations

If there are no material findings, state that explicitly and mention any residual uncertainty or test coverage gaps.
