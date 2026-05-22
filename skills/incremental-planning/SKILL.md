---
name: incremental-planning
description: Create a concise, verifiable implementation plan for non-trivial coding work. Use when scope, dependencies, risk, or validation are not obvious.
---

# Incremental Planning

Break work into small, reviewable, verifiable tasks.

## When to use

Use this skill when:

- The user is in plan mode.
- The request requires multiple code changes, files, steps, or decisions.
- Scope, order, dependencies, data flow, API behavior, or validation are not obvious.
- The work affects behavior, public interfaces, persistence, permissions, performance, or user workflow.
- The task should be split for reviewability or safe incremental implementation.

## When not to use

Do not use this skill when:

- The change is obvious, local, and low risk.
- The user asks for a direct answer, explanation, review, or small edit.
- A clear task breakdown already exists.
- Planning would be longer than the implementation.

## Clarification rule

Before writing the plan document, identify unresolved questions that affect scope, behavior, data model, public API, user intent, validation, or implementation constraints.

If unresolved questions exist:

- Do not write the plan yet.
- Ask only the blocking questions.
- For each question, briefly explain what it affects.
- When useful, include likely options with concise pros and cons.
- Do not make assumptions to proceed.
- Do not include an `Unresolved questions` or `Assumptions` section in the plan document.

If no unresolved questions exist:

- Write the plan document using the output format below.

## Planning rules

- Do not include implementation code in the plan. Reference files, functions, commands, and interfaces only when needed to make the task verifiable.
- Keep the plan concise.
- Prefer vertical slices that leave the system working after each task.
- Order tasks by dependency and risk.
- Each task must be independently understandable, implementable, and verifiable.
- Keep tasks easily reviewable. Prefer small, focused diffs with limited files and one clear concern. Split tasks when the diff becomes hard to understand, verify, or review. Keep tightly coupled changes together when splitting would make the plan less coherent.
- Avoid tasks that mix unrelated concerns.
- Include only files, commands, and checks that are relevant to the implementation.

## Acceptance criteria

Each task must define both:

- Expected behavior: what should happen.
- Non-behavior: what should not happen, regress, or change.

Acceptance criteria must be specific and verifiable. Avoid vague criteria such as “works correctly,” “handles edge cases,” or “improves UX.”

## Output format

```md
# Plan

## Task N: [title]

Goal: [one sentence]

Steps:
- [small implementation step]
- [small implementation step]

Acceptance criteria:
- [ ] Should: [observable expected behavior]
- [ ] Should not: [observable behavior, regression, scope expansion, or side effect that must not occur]

Verification:
- [ ] [test, typecheck, lint, build, or focused manual check]

Likely files:
- `[path]`

...
```