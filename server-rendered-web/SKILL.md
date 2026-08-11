---
name: server-rendered-web
description: Build and improve pragmatic server-rendered web interfaces using semantic HTML, modern CSS, Open Props, HTMX, Alpine.js, and minimal vanilla JavaScript. Use when creating new web interfaces or when working in projects that already use this style. Always preserve and follow an existing project's established frontend stack, conventions, dependencies, and architecture rather than replacing them.
---

# Server-Rendered Web

Build web interfaces with a preference for simple, browser-native, server-rendered architecture.

## First Principle: Respect Existing Projects

Before making architectural or technology choices, inspect the existing repository.

If the project already has an established frontend stack:

- Follow the existing stack and conventions.
- Reuse its existing components, design system, CSS methodology, dependencies, and build tooling.
- Do not introduce Open Props merely because this skill prefers it.
- Do not replace an existing CSS framework or design system.
- Do not migrate an SPA to server rendering.
- Do not replace React, Vue, Svelte, Angular, Tailwind, Bootstrap, or another established technology.
- Do not introduce HTMX or Alpine.js unless they fit naturally into the existing architecture or the user explicitly requests them.
- Make the smallest architectural change necessary to complete the task.

The preferences below are defaults for new projects, new standalone prototypes, or situations where the technology choice is genuinely open.

## Preferred Greenfield Stack

For new web applications and prototypes, prefer:

- Semantic HTML
- Server-rendered HTML
- Modern native CSS
- Open Props for design tokens and reusable CSS primitives
- HTMX for server communication and partial page updates
- Alpine.js for lightweight client-side state and interaction
- Vanilla JavaScript when Alpine.js is unnecessary or inappropriate

Avoid introducing a JavaScript application framework unless explicitly requested or technically justified.

## Open Props

For new projects, use Open Props as the preferred foundation for design tokens and CSS primitives.

Use Open Props for things such as:

- spacing
- sizing
- typography scales
- colors
- shadows
- borders and radii
- easing
- animation timing
- gradients
- layout-related primitives

Treat Open Props as a toolbox rather than a visual design system.

Do not make interfaces look like generic Open Props demos. Build a deliberate visual language appropriate for the product.

Import only what is useful when practical rather than creating unnecessary dependencies.

If an existing project does not use Open Props, do not add it unless the user requests it or introducing it is clearly part of the task.

## HTML

Prefer browser-native semantics.

Use:

- real links for navigation
- real forms for data submission
- buttons for actions
- appropriate heading hierarchy
- semantic structural elements
- native form controls when suitable

Accessibility and keyboard behavior should emerge from correct HTML wherever possible rather than being recreated with JavaScript.

Avoid unnecessary wrapper elements and deeply nested markup.

## Server Ownership

Application state should live on the server by default.

Prefer traditional HTTP request/response behavior and progressively enhance it where useful.

For HTMX requests:

- return the smallest useful HTML fragment
- keep server endpoints understandable outside the frontend
- use HTTP semantics correctly
- use normal server validation
- return meaningful error states
- avoid duplicating server state in JavaScript

Use full-page rendering where partial updates provide no meaningful benefit.

## HTMX

Use HTMX for interactions such as:

- partial content updates
- forms
- search and filtering
- pagination
- modal or drawer content
- inline editing
- dependent controls
- polling
- server-triggered updates

Do not reproduce SPA architecture inside HTMX.

Prefer simple request → HTML response interactions.

Use out-of-band swaps, events, extensions, and advanced HTMX functionality only where they genuinely simplify the implementation.

## Alpine.js

Use Alpine.js for small amounts of local browser state such as:

- menus
- dropdowns
- disclosure controls
- tabs
- temporary UI state
- client-only toggles
- keyboard interaction
- small stateful components

Do not use Alpine.js as a replacement for server-side application state.

If a behavior can be implemented cleanly with HTML or CSS alone, prefer that.

## JavaScript

Use vanilla JavaScript when necessary.

Prefer browser APIs over dependencies.

Do not add a package to solve a problem that can be implemented clearly and safely with a small amount of code.

Avoid introducing:

- React
- Next.js
- Vue
- Nuxt
- Svelte
- Angular
- SPA architecture
- client-side routing
- TypeScript
- Node-based frontend build systems

unless:

1. the existing project already uses them,
2. the user explicitly requests them, or
3. there is a concrete technical requirement that makes them appropriate.

Existing architecture always takes precedence over these preferences.

## CSS

Prefer maintainable native CSS.

Use:

- CSS custom properties
- cascade layers where useful
- grid
- flexbox
- container queries
- logical properties
- modern selectors
- responsive functions such as `clamp()`
- browser-native features where support is appropriate

Use Open Props as the preferred token foundation in greenfield projects.

Do not introduce Tailwind, Bootstrap, another CSS framework, or a CSS-in-JS solution unless requested or already established in the project.

Avoid excessive abstraction for one-off styling.

## Progressive Enhancement

Prefer interfaces that retain sensible behavior with minimal JavaScript.

Start with working HTML and HTTP behavior and enhance where additional interaction improves the experience.

Do not sacrifice simplicity merely to achieve theoretical progressive enhancement when the product requirements clearly need richer behavior.

## Dependencies

Before adding a dependency, consider whether:

- the browser already provides the capability
- the server already provides the capability
- the project already contains a suitable dependency
- the feature is small enough to implement directly

Prefer fewer dependencies and understandable systems.

## Visual Development

When `agent-browser` is available, use it for UI verification.

For meaningful frontend changes:

1. Run the application or open the prototype.
2. Inspect the rendered interface.
3. Check browser console errors.
4. Check relevant browser/runtime errors.
5. Capture screenshots when visual judgment is required.
6. Test relevant interactions.
7. Check important viewport sizes.
8. Iterate when the rendered result does not match the intended design.

Do not launch a visible browser unless explicitly requested.

Use screenshots and visual diffs when they provide useful feedback during iterative design.

## General Philosophy

Prefer:

- simple systems
- explicit behavior
- server-side ownership
- browser-native capabilities
- semantic HTML
- understandable CSS
- minimal client state
- small dependencies
- incremental enhancement

Do not rewrite working architecture simply because this skill would choose differently for a new project.