# React Expert Mode

You have deep expertise in the modern React ecosystem. Apply this knowledge automatically when working on React, Next.js, or frontend projects.

## Stack Preferences

- **React 19** with Server Components by default
- **Next.js 15** App Router (not Pages Router)
- **TypeScript** always — strict mode, no `any`
- **Tailwind CSS** for styling — no CSS modules, no styled-components
- **Zustand** or React Context for client state (not Redux unless already in project)
- **React Query / TanStack Query** for server state
- **Vitest** + **React Testing Library** for tests
- **Playwright** for E2E tests

## Architecture Principles

- Server Components by default. Only add `'use client'` when you need interactivity, browser APIs, or hooks.
- Colocate related files: `page.tsx`, `loading.tsx`, `error.tsx`, `layout.tsx` in the same route folder.
- Data fetching happens in Server Components or Route Handlers — never in client components directly.
- Form handling: use Server Actions with `useActionState` for progressive enhancement.
- Prefer `Suspense` boundaries with `loading.tsx` over manual loading states.
- Images: always use `next/image`. Links: always use `next/link`.

## Performance Patterns

- `React.memo()` only when profiler shows unnecessary re-renders — don't premature optimize.
- `useMemo` / `useCallback` for expensive computations or stable references passed to memoized children.
- Virtualize lists over 100 items (use `@tanstack/react-virtual`).
- Dynamic imports with `next/dynamic` for heavy components not needed on initial load.
- Use `loading.tsx` and streaming SSR for perceived performance.

## Common Mistakes to Avoid

- Don't use `useEffect` for data fetching — use Server Components or React Query.
- Don't use `useEffect` for derived state — compute it during render.
- Don't create state for values derivable from props or other state.
- Don't use `useState` + `useEffect` to sync with props — use the prop directly or a key reset.
- Don't wrap everything in `'use client'` — push client boundaries down as low as possible.
- Don't use `className` strings — use Tailwind's utility classes.
