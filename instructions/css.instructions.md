---
description: CSS, SCSS, and Less best-practice rules for maintainable, accessible, responsive, and performant stylesheets.
applyTo: '**/*.css, **/*.scss, **/*.less'
---

- Prefer logical CSS properties for spacing, sizing, borders, and positioning when values relate to document flow, writing mode, or text direction. Prefer `inset-block-start`, `inset-inline-start`, `margin-block`, `margin-inline`, `padding-block`, and `padding-inline` over physical directional properties such as `top`, `bottom`, `left`, `right`, `margin-top`, `margin-bottom`, `margin-left`, `margin-right`, `padding-top`, `padding-bottom`, `padding-left`, and `padding-right`. Use physical properties only when the placement is intentionally physical, such as viewport anchoring or canvas-like positioning.

- Do not duplicate media queries with the same condition in the same file. Each media query condition should appear once per file. Group all matching rules inside that block, and keep media query blocks ordered from narrowest to widest viewport.

- Do not use hardcoded `px`, `em`, `rem`, `%`, color values, or calculation expressions as design values in component styles. Use existing CSS custom properties or design tokens instead. If a value is component-specific and no shared token exists, define a local custom property with a meaningful name before using it.

- Prefer mobile-first CSS. Define the default styles for the narrowest layout first, then use wider viewport media queries to enhance the layout. Use container queries as progressive enhancements when a component needs to respond to its own container constraints rather than the viewport.

- Animate `transform` and `opacity` by default. For movement animations, prefer `transform: translate(...)` instead of positional or layout properties.

- Avoid animating `top`, `right`, `bottom`, `left`, `width`, `height`, `margin`, `padding`, and `font-size` by default. If animating these properties is necessary, document the reason and ensure the animation does not cause jank, layout shifts, or unnecessary reflow.

- Do not use `position: absolute` solely to move an element during an animation. Use positioning for layout or layering, and use `transform` for animation.

- Avoid deeply nested selectors. Keep selectors shallow, preferably no more than 2–3 levels deep. Prefer stable classes, component scopes, or data attributes over selectors that depend heavily on DOM structure.

- Prefer `rem` for `width`, `height`, `margin`, `padding`, `font-size`, and other properties that should scale with the root font size.

- Avoid using `px` for scalable values. Use `px` only when the value should not scale with the root font size, such as hairline borders, raster image dimensions, or precise third-party integration requirements.

- Use `em` for media query breakpoints when the layout should adapt to the user’s effective font size.

- Use unitless values for `line-height` so line spacing scales appropriately with font size.

- Avoid `text-overflow: ellipsis` for meaningful content. Prefer allowing text to wrap so it remains legible and accessible. Use truncation only when the full content is available elsewhere, such as in adjacent detail text, an accessible label, a tooltip, or an expanded state.

- Avoid `!important`. Prefer resolving cascade issues through better source order, cascade layers, component boundaries, or lower-specificity selectors. Use `!important` only for documented exceptions such as utility classes, accessibility fixes, third-party CSS overrides, or emergency fixes with a follow-up task.