# code-reviewer-skill

Standalone skill repository for structured code review workflows.

Main skill path:
- `skills/code-reviewer/`

This repository is intentionally focused on skill assets:
- `SKILL.md` for workflow and invocation guidance
- `references/` for scenario-specific review checklists
- `scripts/` for deterministic diff helpers
- `agents/openai.yaml` for UI metadata

Design goals:
- cross-platform helper scripts based on Python 3 standard library
- language-aware review output that defaults to the user's language
- no dependency on a specific code hosting platform for the core skill

Release notes for the current version:
- supports snippet, diff, commit, PR, and MR review flows
- includes security-focused review guidance
- includes optional GitHub PR and GitLab MR review references
- ships portable Python helper scripts for diff normalization, splitting, and summary preparation
