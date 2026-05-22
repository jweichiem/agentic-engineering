---
description: TypeScript best-practice rules for type safety, narrowing, public boundaries, and avoiding unsafe escape hatches.
applyTo: '**/*.{ts,tsx}'
---

- Do not use `any`. This includes explicit `any`, implicit `any`, `Promise<any>`, `Array<any>`, `Record<string, any>`, rest parameters typed as `any[]`, and generic defaults or constraints that erase type information.

- Use `unknown` instead of `any` for values from external or untrusted boundaries such as JSON, network responses, storage, environment variables, messages, URL params, third-party callbacks, and loosely typed libraries. Validate or narrow the value before using it.

- Add runtime validation at external boundaries when TypeScript cannot prove the shape of the data. Prefer existing project validators, schema helpers, or focused type guards over unchecked casts.

- Avoid type assertions with `as` unless TypeScript lacks information that the code has already established. Keep assertions local, specific, and backed by a nearby check or invariant.

- Do not use double assertions such as `value as unknown as TargetType` unless integrating with an unavoidable third-party typing gap. Document why the assertion is safe when it is necessary.

- Do not suppress type errors with `@ts-ignore` or `@ts-expect-error` unless there is no practical typed alternative. Include a short explanation and keep the suppressed line as narrow as possible.

- Prefer precise domain types over broad catch-all types. Avoid `object`, `{}`, `Function`, `unknown[]`, and stringly typed bags when the allowed shape, keys, or callback signature is known.

- Prefer discriminated unions for values with variants. Use literal discriminants and exhaustive checks so adding a variant creates useful compiler errors.

- Model optional and nullable values explicitly. Narrow with control flow before use instead of relying on non-null assertions (`!`) or broad fallback casts.

- Let TypeScript infer local variable and return types when the expression is clear. Add explicit types for exported functions, public APIs, component props, shared data structures, and values where inference would hide an important contract.

- Use generics to preserve input and output relationships in reusable helpers. Do not replace generic relationships with `any` or unrelated broad types.

- Type arrays, tuples, maps, and records with the narrowest useful element, key, and value types. Use `Record<string, unknown>` only when keys are truly open and values must be narrowed before use.

- Prefer `readonly` arrays, tuples, and object properties for inputs that should not be mutated. Do not mutate typed inputs unless the function contract clearly owns that mutation.
