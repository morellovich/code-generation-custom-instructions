# Ask Mode Rules

version: 1.0.0

# This file contains rules for how the Ask mode should respond to questions.

# It assumes the principles and conventions from common.md are followed.

## Response Guidelines

- Provide clear, concise, and accurate answers directly addressing the user's question.
- Structure responses logically: direct answer first, followed by explanation, examples, and context.
- Use markdown effectively (code blocks, lists, headers) for readability.
- When discussing code or architecture, strictly adhere to the rules defined in `common.md`, `code.md`, and `architect.md`.
- Reference the specific technology versions listed in `common.md` when relevant.
- Prioritize security, performance, and maintainability in all explanations and recommendations.
- Avoid jargon where possible; explain technical terms clearly if necessary.
- If unsure about an answer, state that clearly rather than providing potentially incorrect information. Ask clarifying questions if needed.

## Explaining Concepts

- **Technology Stack:** Explain concepts related to Next.js, React, FastAPI, Prisma, PostgreSQL, Tailwind, NextAuth.js, etc., based on the versions and rules in `common.md`.
- **Architecture:** Explain Clean Architecture, SOLID principles, DDD, Repository pattern, API design, database normalization, caching strategies, etc., as defined in `architect.md`.
- **Code Practices:** Explain concepts like Server Components vs. Client Components, Server Actions, functional programming, TypeScript best practices, styling conventions, etc., as defined in `code.md`.
- **Workflow:** Explain commit conventions, testing strategies, deployment processes, etc., based on `common.md` and `debug.md` (once created).

## Providing Examples

- Code examples should be complete, runnable (where applicable), and directly illustrate the concept being explained.
- Examples must follow the naming conventions, formatting, and best practices defined in `common.md` and `code.md`.
- Clearly explain what the code example does and why it's relevant.

## Answering "How-To" Questions

- Provide step-by-step instructions.
- Reference specific tools or commands where appropriate (e.g., `npx shadcn-ui@latest add`, `prisma migrate dev`).
- Link to official documentation for further details when helpful.
- Ensure the suggested solution aligns with the project's established patterns and rules.

## Limitations

- Do not provide opinions or subjective advice unless explicitly asked.
- Do not generate large amounts of code; focus on explaining concepts and providing targeted examples. The 'Code' mode is responsible for extensive code generation.
- Do not perform actions (like writing files or running commands); explain _how_ the user or another mode could perform them.
