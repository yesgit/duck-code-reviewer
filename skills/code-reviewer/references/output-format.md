# Output Format

Use this structure for the final review.

```md
## Summary
- Brief description of what changed
- Overall assessment in one sentence

## Findings

### High
- Location: <file/symbol/hunk or "unknown">
  Issue: <what is wrong>
  Impact: <why it matters>
  Recommendation: <what to change>

### Medium
- ...

### Low
- ...

### Info
- ...

## Risk Assessment
- Overall risk: <low|medium|high>
- Confidence: <low|medium|high>
- Main uncertainty: <if any>

## Score
- Score: <1-10>/10

## Top Recommendations
1. <highest-value fix>
2. <second-highest-value fix>
3. <third-highest-value fix>
```

## Rules

- If a severity level has no findings, omit that section.
- If there are no material findings, say so under `Findings` and still include residual risk or uncertainty.
- Keep findings concrete and concise.
- Avoid speculative claims without stating uncertainty.
