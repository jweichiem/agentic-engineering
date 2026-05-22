---
name: incremental-implementation
description: Execute an approved plan incrementally. Use when implementing one task or slice from a plan.
---

# Incremental Implementation

Implement one small, verifiable slice at a time.

## When to use

Use this skill when:

- The user asks to implement, execute, continue, or complete a task from an approved plan.

## Before implementing

- Identify the single plan task or coherent slice to implement.
- Confirm the task has clear acceptance criteria and verification steps.
- If the task is ambiguous or lacks acceptance criteria, stop and ask for clarification before changing code.
- Inspect existing code for matching helpers, patterns, tests, and conventions before writing new logic.
- Keep the task scope fixed. Do not add adjacent cleanup, refactors, features, or new abstractions.

## Implementation rules

- Implement only one task or coherent slice at a time.
- Keep changes small, focused, and easy to review.
- Prefer the simplest correct implementation that satisfies the task acceptance criteria.
- Do not introduce abstractions, configurability, dependencies, public APIs, environment variables, or cross-cutting patterns unless required by the approved task or existing architecture.
- Reuse existing helpers, types, components, styles, tests, and project patterns when they fit.
- Add validation and error handling at external or trust boundaries.
- Do not add defensive checks for invariants already enforced locally.
- Keep tightly coupled changes together when splitting would reduce clarity.
- Stop and ask to split the task when the change mixes unrelated concerns, touches unrelated areas, or becomes hard to verify.
- Keep the system working after each slice.

## Validation

After each implemented slice:

- Run the narrowest relevant verification from the plan.
- Prefer focused tests, typechecks, lint checks, builds, or manual checks that directly validate the changed behavior.
- Do not rerun the same command unless code changed since the last successful run.
- If validation cannot be run, state what was not run and why.
- Do not proceed to the next slice while the current slice is failing unless the user explicitly chooses to continue.

## Completion response

After implementing a slice, use this format:

```md
## Completed

- [brief summary of what changed]

## Acceptance criteria

- [criterion]&#58; satisfied by [specific change]

## Validation

- [command/check]&#58; [result]

## Manual verification

- [step-by-step way to verify criterion 1]
- [step-by-step way to verify criterion 2]

## Review notes

- [anything to inspect carefully, or "None"]

## Not validated

- [anything not validated, or "None"]

## Next task

- [next remaining plan task, if relevant]