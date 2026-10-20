# Failure-Driven Improvement

> Turn coding failures into verified Markdown playbooks that any coding harness can reuse.

## Why this exists

Coding harnesses such as Codex, Claude Code, and others can solve the problem in front of them. But the investigation and lessons often stay in a chat. When a similar issue appears later—or a different harness is used—the same work may have to be repeated.

Failure-Driven Improvement (FDI) gives that knowledge a durable, searchable home in Markdown files.

## What it is

FDI is a **harness-agnostic workflow and playbook format** for capturing failures, their evidence, and the fixes that resolved them. The records can live in version control and be read by different coding tools without depending on one vendor's memory feature.

A playbook should explain more than the final change. It should preserve the conditions that caused the failure, how it was diagnosed, what fixed it, how the fix was verified, and where the guidance applies.

## The FDI loop

1. **Look up** relevant playbooks before investigating a failure.
2. **Investigate** the current problem. Treat a playbook as a useful lead, not proof that the same cause applies.
3. **Fix and verify** the problem in the current project and environment.
4. **Record** each failure and its outcome. Keep observations separate from hypotheses; label an unconfirmed cause or fix as suspected.
5. **Reuse and maintain** the playbook later. Update it when new evidence changes its diagnosis, steps, or applicability.

## Playbook format

Keep entries short enough to scan and detailed enough to reproduce. A starting template:

```markdown
# [Short failure title]

- Last verified: YYYY-MM-DD
- Applies to: [project, component, version, harness, or environment]

## Symptom
What happened? Include the exact error or observable behavior.

## Evidence
Relevant command, log excerpt, or reproduction steps.

## What was tried
Approaches that failed and what they showed.

## Cause
Verified explanation, or mark it as suspected.

## Fix
The change or steps that resolved the failure.

## Verification
The check that passed and its result.

## Boundaries
When this guidance applies, and when it may not.

## Related playbooks
Links to nearby cases.
```

Do not put secrets, credentials, or customer data in playbooks. Redact sensitive values from logs and examples.

## Use with any coding harness

A compatible harness should search the shared playbooks before repeating known troubleshooting, check that a record's assumptions match the current project, verify any suggested fix, and write back new failure knowledge in the same Markdown format.

Harness-specific setup may be needed to make a tool find and update the files. The playbooks remain the shared source of truth, so one harness's private memory is not required.

## Why Markdown

Markdown is plain text: easy to review in a diff, edit by hand, search, and keep in version control. It keeps the knowledge portable across models, harnesses, and repositories.

A common starting layout is:

```text
playbooks/
├── index.md
└── <area>/
    └── <failure-name>.md
```

## A path toward smaller models

A frontier model can help investigate a new failure and turn the confirmed diagnosis into clear, reusable steps. Later, a smaller model may be able to resolve a known case by finding and following those steps.

This is a goal to evaluate, not a guarantee. Playbooks do not train a model or make it remember across tasks. They provide external context; the model and harness still need to retrieve the relevant entry, check its assumptions, and verify the result.

## Current status

This repository currently describes the FDI approach. Automated failure capture and harness-specific integrations are not included yet.
