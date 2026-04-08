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
- includes architecture, design, and standards review with hierarchical rule precedence
- includes baseline design inference from existing code when explicit docs are incomplete
- ships portable Python helper scripts for diff normalization, splitting, and summary preparation

## Install

Copy the skill directory into your local Codex skills folder:

```bash
mkdir -p ~/.codex/skills
cp -R skills/code-reviewer ~/.codex/skills/
```

After installation, the skill path should look like:

```text
~/.codex/skills/code-reviewer/
```

## What It Can Review

- code snippets and files
- git diffs and patches
- commits
- pull requests and merge requests
- security-focused changes
- architecture, design, and standards violations
- drift from existing implicit design conventions

## Output Style

The skill can produce:
- a compact `1-10` score for lightweight review
- a weighted `0-100` scorecard for larger diffs, commits, PRs, MRs, and chunk-merged reviews

It also supports review styles:
- `professional`
- `gentle`
- `sarcastic`
- `humorous`
- `random`

## Language Behavior

- If the request is in Chinese, the review defaults to Chinese.
- If the request is in English, the review defaults to English.
- Code, identifiers, paths, and commands remain untranslated.

## Quick Start

Snippet review:

```text
Use $code-reviewer to review this Python code for correctness and edge cases:

def divide(a, b):
    return a / b
```

Diff review:

```text
Use $code-reviewer to review this diff in Chinese:

diff --git a/app.py b/app.py
--- a/app.py
+++ b/app.py
@@ -1,2 +1,4 @@
 def login(user, password):
-    return check(user, password)
+    if user:
+        return True
+    return False
```

Security review:

```text
Use $code-reviewer to do a security-focused review of this code in English:

def run(cmd):
    os.system(cmd)
```

Architecture and standards review:

```text
Use $code-reviewer to review whether this diff violates project architecture or local directory rules. Check README.md, docs/, CLAUDE.md, AGENTS.md, .cursorrules, and .cursor/rules/ with nearest-directory rules overriding parent defaults.
```

Design inference review:

```text
Use $code-reviewer to infer the existing design conventions from the old codebase, then check whether this new code or diff drifts from those established patterns.
```

## Examples

See [`examples/`](./examples/) for small test inputs you can paste directly into a prompt.

## Repository Layout

```text
code-reviewer-skill/
├── skills/code-reviewer/
│   ├── SKILL.md
│   ├── agents/openai.yaml
│   ├── references/
│   └── scripts/
└── examples/
```
