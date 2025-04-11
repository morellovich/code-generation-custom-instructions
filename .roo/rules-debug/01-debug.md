# Debug Mode Rules

version: 1.0.0

# This file contains rules for debugging, testing, and error handling.

# It assumes the principles and conventions from common.md are followed.

## Systematic Debugging Approach

1.  **Identify & Understand:**
    - Analyze error messages, stack traces, and logs carefully.
    - Determine if the issue is client-side, server-side, build-time, or runtime.
    - Reproduce the issue consistently. If intermittent, gather more context (user actions, time, environment).
2.  **Isolate:**
    - Narrow down the issue to the smallest possible code section (component, function, module).
    - Use browser DevTools (breakpoints, console logs, network inspector) for frontend issues.
    - Use server-side logging and debugging tools (e.g., Python debugger) for backend issues.
    - Comment out code sections systematically to pinpoint the faulty part.
    - Create a minimal reproducible example if necessary.
3.  **Analyze Root Cause:**
    - Consult common issues sections below (Next.js, React, API, DB, Auth).
    - Check for recent code changes that might have introduced the bug.
    - Verify environment differences (dev vs. prod).
    - Validate assumptions about data, state, or external services.
4.  **Implement & Verify Fix:**
    - Apply the most direct and correct fix for the root cause.
    - Test the fix thoroughly in the development environment.
    - Add specific unit or integration tests to cover the bug and prevent regression.
    - Consider potential side effects of the fix.

## Error Handling Best Practices

- Implement proper error boundaries (`error.tsx` in Next.js) to gracefully handle rendering errors in UI segments.
- Use `try/catch` blocks specifically for operations prone to failure (API calls, DB queries, file I/O, browser APIs).
- Implement structured logging (using Sentry/Pino/Winston) for all errors, including relevant context (user ID, request details, state).
- Provide user-friendly error messages that don't expose sensitive system details.
- Implement graceful fallbacks or alternative flows when errors occur (e.g., showing cached data if a fetch fails).
- Ensure consistent error response formats from APIs (e.g., `{ "error": { "code": "AUTH_FAILED", "message": "Invalid credentials" } }`).

## Common Issues & Checks

### Next.js / React

- **Hydration Errors:** Check for mismatches between server-rendered and client-rendered output. Ensure browser-only APIs are used within `useEffect` or conditional checks. Verify `key` props in lists.
- **Hook Rules:** Ensure hooks are called at the top level, not inside loops, conditions, or nested functions. Check dependency arrays in `useEffect`, `useCallback`, `useMemo`.
- **State Management:** Verify state updates are immutable. Check for race conditions in async state updates. Ensure state is lifted appropriately.
- **Server/Client Components:** Confirm Client Components (`"use client";`) are used only when necessary (hooks, browser APIs, interactivity). Ensure data fetching happens in Server Components or Server Actions.
- **Server Actions:** Check for missing `await`, unhandled promise rejections, and proper error/loading state handling.
- **Cleanup:** Ensure event listeners, timers, or subscriptions created in `useEffect` are cleaned up in the return function.

### TypeScript

- Check for type mismatches (`strictNullChecks`!). Use type guards or assertions carefully.
- Verify interface/type definitions match actual data structures.
- Avoid using `any` type; use `unknown` and perform type checking.

### API / Backend (FastAPI)

- Check CORS configuration (`allow_origins`, `allow_methods`, `allow_headers`).
- Verify error handling in `async def` routes; ensure exceptions are caught and handled.
- Check Pydantic model validation errors.
- Ensure background tasks don't block responses and handle their own errors.
- Verify dependency injection (`Depends`) setup.

### Database (PostgreSQL / Prisma)

- Check for N+1 query problems; use `include` or `select` in Prisma queries.
- Verify transaction logic ensures atomicity.
- Analyze slow queries using `EXPLAIN ANALYZE`; check for missing indexes.
- Ensure database connection pooling is configured correctly.
- Verify Prisma schema matches the database structure (`prisma db pull`, `prisma migrate dev`).
- Check for constraint violations (unique, foreign key, not null).

### Authentication (NextAuth.js)

- Verify `NEXTAUTH_URL` and `NEXTAUTH_SECRET` environment variables.
- Check session handling (database adapter, JWT settings).
- Ensure middleware (`middleware.ts`) correctly protects routes.
- Debug provider configurations (credentials, OAuth client IDs/secrets).
- Check cookie settings (`secure`, `httpOnly`, `sameSite`).
- Verify CSRF token handling.

## Testing for Bugs

- Write specific unit tests (Jest/Pytest) to reproduce the bug before fixing it (TDD approach).
- Add integration tests to verify interactions between components or services related to the bug.
- Use E2E tests (Playwright) to simulate the user scenario that triggered the bug.
- Ensure tests cover edge cases related to the fix.

## Monitoring & Logging (Sentry)

- Ensure Sentry SDK is correctly configured for both frontend and backend.
- Use breadcrumbs to track user actions leading up to an error.
- Set user context (ID, email) for easier error correlation.
- Implement source maps for accurate stack traces in production.
- Mask sensitive data in logs and Sentry reports.
- Create alerts in Sentry for critical error types or frequency spikes.

## Debugging Tools

- **Frontend:** Browser DevTools (Elements, Console, Network, Application tabs), React DevTools extension.
- **Backend:** Python debugger (pdb, VSCode debugger), FastAPI interactive docs (`/docs`), database query logs, `EXPLAIN ANALYZE`.
- **E2E:** Playwright Inspector, trace viewer, video recording.
- **General:** Structured logging viewers, Sentry dashboard.
