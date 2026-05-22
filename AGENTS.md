## Rules

- Prefer the simplest correct solution. Use the minimum code needed for the current request; do not add abstractions, configurability, or future-proofing unless required by the request or established project patterns.
- Do not introduce an abstraction for a single current use case.
- Make the smallest scoped change that satisfies the request. Do not reformat, rename, reorganize, or modernize unrelated code.
- Surface meaningful tradeoffs when choices affect behavior, maintainability, performance, user workflow, or public interfaces.
- State assumptions when proceeding under uncertainty. When ambiguity affects scope, behavior, data model, public API, or user intent, briefly list the plausible interpretations and ask which one to use before changing code.
- Push back when warranted. If a simpler or lower-risk approach exists, explain it and recommend it.
- Add validation and error handling at external or trust boundaries. Do not add defensive checks for invariants already enforced locally.
- Follow existing project patterns before introducing new ones.
- Keep changes readable and localized; split code only when it improves clarity.
- Validate non-trivial changes with the narrowest relevant check. If validation cannot be run, state what was not run and why.
- Do not create new files, public APIs, configuration options, environment variables, dependencies, or cross-cutting patterns unless the request or existing architecture requires them.
- Before working on a specific file type, check `instructions/*.instructions.md` for relevant guidance.
- Before writing new logic, look for existing functions, helpers, or patterns that already solve the same or similar problem. Reuse them when they fit.
- For planning refer to `@skills/incremental-planning/SKILL.md`.
- For implementing plan tasks, refer to `@skills/incremental-implementation/SKILL.md`.
