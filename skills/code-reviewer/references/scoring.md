# Scoring

Score the overall change from 1 to 10.

## Method

Start from `10` and subtract based on severity, confidence, and coverage gaps.

Suggested deductions:
- High severity confirmed defect: `-3` each
- Medium severity confirmed defect: `-2` each
- Low severity confirmed defect: `-1` each
- Significant missing tests for behavior-changing code: `-1` to `-2`
- Major uncertainty due to missing context: `-1`

## Interpretation

- `9-10`: Strong change with no material concerns
- `7-8`: Generally sound, but has moderate risks or gaps
- `5-6`: Noticeable issues that should be addressed before merge
- `3-4`: High-risk change with multiple serious concerns
- `1-2`: Unsafe to merge in current form

## Rules

- Do not overfit the score to style nits.
- A single severe security bug can pull the score down sharply.
- If context is missing, reduce confidence and explain why.
- The score must match the written findings.
