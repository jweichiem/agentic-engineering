---
description: React 19 best-practice rules for component structure, hooks, state, effects, rendering, performance, and server/client boundaries.
applyTo: '**/*.{jsx,tsx}'
---
- Prefer `const` arrow functions for React components, custom hooks, event handlers, callbacks, and helper functions. Do not use function declarations unless the function must be a generator using `function*`.

- Keep components pure. Do not cause side effects during render, mutate props, mutate state, mutate external values, or read changing browser globals during render.

- Keep components small and focused. Split components when JSX, state, effects, or conditional rendering become difficult to scan.

- Prefer composition over configuration-heavy components. Avoid many boolean props or mode props that create unrelated rendering branches.

- Keep state minimal, local, and derived where possible. Lift state only when components need to coordinate, and do not store values that can be calculated from props, state, or context.

- Do not mutate state directly. Create new arrays, objects, Maps, and Sets when updating React state.

- Avoid unnecessary Effects. Use Effects only to synchronize with external systems such as browser APIs, subscriptions, timers, analytics, network connections, or third-party widgets. Clean up Effects that subscribe, schedule timers, attach listeners, observe DOM, or open connections.

- Follow the Rules of Hooks. Call hooks only at the top level of React components or custom hooks, never inside loops, conditions, nested functions, callbacks, `try`/`catch`/`finally`, class components, or regular JavaScript functions.

- Define custom hooks only for reusable stateful behavior. If a function does not call React hooks, do not name it with the `use` prefix.

- Do not overuse `useMemo`, `useCallback`, or `memo`. Use them only for expensive calculations, stable dependencies, or measured rendering issues.

- Use stable keys for lists. Do not use array indexes as keys when items can be inserted, removed, reordered, filtered, or edited.

- Prefer CSS for transitions and animations. React should toggle state, class names, and attributes; CSS should define the visual transition. Use React-driven animation only when CSS cannot express the interaction cleanly.

- Protect LCP by rendering above-the-fold UI from initial props, server data, or already-available state. Do not rely on `useEffect` to fetch, compute, or reveal the primary page content.

- Do not lazy-load likely LCP components or assets. Prioritize hero images, primary headings, and key above-the-fold content; lazy-load only content that is below the fold or interaction-only.

- Keep route entry components lightweight. Move heavy components, large dependencies, charts, editors, maps, media players, and third-party widgets behind dynamic imports when they are not required for the initial view.

- Protect INP by keeping React updates caused by user input small and focused. Avoid large synchronous renders, expensive derived calculations, and broad state updates in input, click, keyboard, pointer, and scroll handlers.

- Avoid layout shifts from React state changes. Reserve space before rendering async content, validation messages, banners, images, embeds, skeletons, and conditionally mounted UI.

### Server-Side Rendering Rules

- In server-rendered or React Server Component environments, prefer server-rendered components for static, content-heavy, data-fetching, and above-the-fold UI. Use client rendering only when the component needs browser APIs, local interactivity, client state, effects, or event handlers.

- Keep Client Component boundaries as small as possible. Do not mark large route trees, layouts, or shared wrapper components as client-rendered unless the whole subtree truly requires client-side behavior.

- Pass only serializable data from Server Components to Client Components. Do not pass functions, class instances, non-serializable objects, or server-only values across the server/client boundary.

- Avoid hydration mismatches. Do not render different initial markup on the server and client using `Date.now()`, `Math.random()`, locale-sensitive formatting, browser-only state, viewport size, or `localStorage` during the initial render. Use stable server-rendered values, placeholders, or explicit client-only boundaries when values are only available in the browser.