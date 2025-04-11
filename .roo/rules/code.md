# Code Mode Rules

version: 1.0.0

# This file contains rules specific to generating and modifying code.

# It assumes the principles and conventions from common.md are followed.

## General Code Generation

- Every time you apply a rule(s), explicitly state the rule(s) in the output. Abbreviate the rule description to a single word or phrase (e.g., "Rule: DRY", "Rule: Functional Component").
- Replace class components with functional components using React Hooks.
- Use Server Components by default. Only use Client Components ("use client";) when interactivity requiring browser APIs or React state/lifecycle hooks (useState, useEffect, etc.) is essential. Keep Client Components small and push state down.
- Implement React Server Actions for data mutations (form submissions, updates, deletions) instead of creating client-side API fetching logic.
- Use Next.js Route Handlers (`src/app/api/.../route.ts`) only for cases where Server Actions are unsuitable (e.g., webhook endpoints, specific API integrations requiring custom response/request handling).
- Implement structured logging (e.g., using Pino or Winston, integrated with Sentry) to simplify debugging and error tracking. Log key events, errors, and context.
- Use explicit `try/catch` blocks _only_ for operations prone to failure:
  - External API calls (fetch, axios)
  - File system operations (fs module)
  - Database queries (Prisma client calls)
  - Browser-specific APIs (localStorage, navigator) - _Ensure these are only in Client Components._
- Use explicit return types for all functions, including arrow functions, to improve type safety and readability.
- Use absolute imports starting with `@/` configured in `tsconfig.json` (e.g., `@/components/Button`).

## TypeScript Specifics

- Enable and adhere to TypeScript's `strict` mode in `tsconfig.json`.
- Prefer `interface` over `type` for defining object shapes or implementing classes. Use `type` for unions, intersections, primitives, or more complex types.
- Avoid `enum`; use string literal unions or `as const` objects instead for better tree-shaking and JavaScript output.
  ```typescript
  // Instead of: enum Status { Pending, Completed }
  type Status = "pending" | "completed";
  // Or:
  const Status = { Pending: "pending", Completed: "completed" } as const;
  type Status = (typeof Status)[keyof typeof Status];
  ```
- Use `unknown` instead of `any` when the type is genuinely unknown, and perform type checking before use.
- Utilize utility types (Partial, Required, Pick, Omit, Readonly) to create new types from existing ones.

## React / Next.js Specifics

- Use functional components and React Hooks.
- Use Server Components by default for data fetching and rendering static content.
- Use Client Components (`"use client";`) for interactivity, state, lifecycle hooks, and browser APIs.
- Wrap Client Components that suspend (e.g., during data fetching) in `<Suspense>` with an appropriate fallback UI.
- Use the `next/image` component for all images, providing `width`, `height`, and `alt` props. Use `fill` prop for background images or when aspect ratio is unknown. Optimize images (format: webp, quality).
- Use the Metadata API (`export const metadata = {...}`) in `layout.tsx` and `page.tsx` for SEO.
- Implement dynamic imports (`next/dynamic`) for components that are not needed immediately or are large, especially in Client Components.
- Use Server Actions for form submissions and data mutations. Handle loading and error states within the action or calling component.
- Implement proper error handling using `error.tsx` files for route segments and `try/catch` within Server Actions/Route Handlers.
- Use React Context sparingly, primarily for global state like theme, authentication status, or app-wide settings. Avoid using it for frequently changing data.
- Use `React.memo` for Client Components only when profiling shows significant performance gains are needed due to frequent re-renders with unchanged props.
- Use `useCallback` for functions passed as props to memoized child components to prevent unnecessary re-renders.
- Use `useMemo` only for computationally expensive calculations, not for memoizing simple values or components.
- Always provide a `key` prop when rendering lists of elements. Use stable, unique identifiers (like database IDs) as keys. Avoid using array indices as keys if the list can change order.

## UI & Styling (Tailwind CSS / Shadcn UI)

- Use Shadcn UI components (`npx shadcn-ui@latest add [component]`) as the primary component library.
- Apply styling primarily using Tailwind CSS utility classes.
- Keep utility classes organized and apply them directly to JSX elements. Avoid creating custom CSS classes unless absolutely necessary for complex scenarios not covered by Tailwind.
- Use Tailwind's responsive modifiers (`sm:`, `md:`, `lg:`) for mobile-first responsive design.
- Use Tailwind theme configuration (`tailwind.config.js`) to customize colors, fonts, spacing, etc., instead of arbitrary values.
- Avoid excessive nesting of styled elements; prefer composition.
- Use `@apply` sparingly in CSS files, only for reusable component patterns not achievable with utilities alone.

## FastAPI Specifics

- Use `async def` for all route handlers to ensure non-blocking I/O.
- Use Pydantic models for request body validation and response serialization. Define clear schemas.
- Implement dependency injection (`Depends`) for reusable logic (e.g., database sessions, authentication checks).
- Use background tasks (`BackgroundTasks`) for operations that don't need to block the response (e.g., sending emails).
- Implement structured error handling using custom exception handlers to return consistent error responses.
- Automatically generate OpenAPI documentation (`/docs`, `/redoc`) and ensure it's accurate.

## Prisma Specifics

- Use Prisma Client for all database interactions.
- Use transactions (`prisma.$transaction([...])`) for operations involving multiple dependent writes to ensure atomicity.
- Prevent N+1 query problems by using `include` or `select` appropriately when fetching related data.
- Use parameterized queries implicitly provided by Prisma Client to prevent SQL injection.
- Use Prisma Migrate (`prisma migrate dev`, `prisma migrate deploy`) to manage database schema changes. Create descriptive migration names.
- When adding/modifying fields, update `schema.prisma` and run `prisma migrate dev`.
- Filter queries for soft deletes (`where: { deletedAt: null }`).

## Testing Integration

- After generating or modifying code for a feature, ensure corresponding unit tests (Jest/Pytest) and/or E2E tests (Playwright) are created or updated.
- Write tests covering primary functionality, edge cases, and error conditions.
- Use fixtures (Pytest) or setup/teardown functions (Jest) for test setup.
- Ensure tests are independent and do not rely on the state of previous tests.
