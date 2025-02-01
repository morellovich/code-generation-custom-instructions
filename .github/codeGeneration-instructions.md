## Instructions for General Code Generation

    - Every time you choose to apply a rule(s), explicitly state the rule(s) in the output. You can abbreviate the rule description to a single word or phrase.
    - Follow DRY (Don't Repeat Yourself) and KISS (Keep It Simple, Stupid) principles for maintainability.
    - Ensure code readability with consistent indentation, spacing, and meaningful names.
    - Replace class components with functional components
    - Use Server Components by default
    - Implement React Server Actions instead of client-side API calls
    - Use route handlers instead of API routes where possible
    - Write modular, reusable code to improve flexibility and testability.
    - Implement structured logging to simplify debugging and error tracking.
    - Use error handling and graceful fallbacks to improve reliability and availability.
    - Prioritize security: sanitize inputs, follow least privilege principles, and enforce authentication.
    - Optimize performance by reducing redundant computations and unnecessary API calls.
    - Ensure cross-platform compatibility and avoid framework-specific dependencies when possible.
    - Write comprehensive tests to validate functionality and catch regressions early.
    - Design scalable and efficient architectures to support future growth.
    - Use functional and declarative programming patterns; avoid classes when possible.
    - Prefer iteration and modularization over code duplication.
    - Create separate files for framework-specific rules
    - Maintain a single source of truth for common rules
    - Include decision trees for technical choices
    - Create an index file linking to specific instruction sets
    - Use a hierarchical structure for related rules
    - Implement versioning for instruction sets

## Preferred Technology Stack and Versions

    - You are an expert senior developer in the following languages, generate code using ONLY the following technologies and their specified versions:

**Frontend:**

    - Next.js:Version 15.1.6
    - Tailwind CSS:Version 4.0.1
    - React Native:Version 0.77.0

**Backend:**

    - FastAPI:Version 0.115.7

**Database:**

    - PostgreSQL:Version 17.2

**ORM:**

    - Prisma:Version 6.3.0

**Authentication:**

    - NextAuth.js (Auth.js):Version 4.24.11

**Testing:**

    - Jest:Version 29.7.0
    - React Testing Library:Version 16.2.0
    - Pytest:Version 8.3.4

**Logging and Monitoring:**

    - Sentry SDK for JavaScript:Version 7.59.0
    - Sentry SDK for Python:Version 1.29.2

**Containerization and Deployment:**

    - Docker:Version 27.5.1
    - Coolify:Version 4.0.0-beta.389

## Instructions for Next.js / TypeScript Code Generation

    - Use functional components and React hooks for clean, reusable code.
    - prefer interfaces over types.
    - Avoid enums; use maps instead.
    - Optimize state management for smooth page transitions and user interactions.
    - Use absolute imports for all files @/...
    - Use try/catch only for:
        - External API calls
        - File operations
        - Database queries
        - Browser API interactions
    - Use explicit return types for all functions
    - Add Edge Runtime considerations
    - Include Server Actions guidelines
    - Add streaming and progressive rendering rules
    - Add TypeScript strict mode requirements
    - Include Web Vitals metrics requirements
    - Add accessibility (a11y) requirements
    - Include API versioning strategy

## Instructions for Tailwind CSS Code Generation

    - Keep utility classes organized and meaningful for better maintainability.
    - Avoid excessive nesting to reduce CSS bloat and improve performance.
    - Prefer responsive, reusable styles over inline custom styles.

## Instructions for React Native Code Generation

    - Prioritize component reusability and use TypeScript for type safety.
    - Maintain a clear project structure for easier testing and debugging.
    - Optimize network requests using caching and background sync where applicable.
    - Use React Context only for theme, auth, and app-wide preferences
    - Implement Server Components and Server Actions for data management"
    - Implement proper cleanup in useEffect hooks

## Instructions for FastAPI Code Generation

    - Use async functions for scalable, non-blocking API handling.
    - Implement structured error handling for secure and reliable endpoints.
    - Ensure OpenAPI documentation is generated for better API usability.

## Instructions for PostgreSQL Code Generation

    - Follow normalization principles and use indexes for query optimization.
    - Implement failover mechanisms and automated backups for high availability.
    - Enforce role-based access control (RBAC) to protect sensitive data.

## Instructions for Prisma Code Generation

    - Maintain consistent model and field naming conventions for clarity.
    - Use transactions for handling complex operations safely.
    - Include mock data and transactional tests for database reliability.
    - Use parameterized queries to prevent SQL injection.
    - Apply indexing strategies for performance tuning.
    - Ensure foreign keys and constraints are correctly defined.
    - Always use migrations to update the database schema
    - When adding a new field to a table, add it to the migration file and update the schema file
    - When changing db models, add a migration file and update the schema file (in src/lib/migrations/) it should follow the naming convention of the other migration files

## Instructions for NextAuth.js (Auth.js) Code Generation

    - Define authentication flows, including session management and token storage.
    - Implement CSRF protection and secure cookie settings for security.
    - Ensure support for OAuth, JWT, and multi-factor authentication (MFA).

## Instructions for Jest, React Testing Library & Pytest Code Generation

    - Write comprehensive tests covering edge cases and unexpected inputs.
    - Use fixtures for setup/teardown in Pytest to streamline testing.
    - Ensure clear test descriptions for better maintainability and debugging.

## Instructions for Sentry Code Generation

    - Implement error tracking with environment-specific configurations.
    - Use breadcrumbs and user context for detailed error reports.
    - Ensure sensitive data masking to comply with privacy standards.
    - Integrate logging using the specified Sentry SDKs to monitor and debug applications effectively.

## Instructions for Docker Code Generation

    - Use optimized base images and multi-stage builds to reduce size.
    - Implement health checks and restart policies for stable containers.
    - Define environment variables properly to improve security and flexibility.

## Stick to this folder structure for all repositories:

    src/
    ├── core/ # Business logic (reusable across backend/frontend)
    │ ├── domain/ # Business entities & validation rules
    │ ├── usecases/ # Application logic & services
    │ ├── interfaces/ # Abstract interfaces for business rules
    ├── infrastructure/ # System-level implementations
    │ ├── database/ # PostgreSQL & Prisma implementations
    │ ├── external/ # API integrations (e.g., Auth, Sentry)
    │ ├── storage/ # File & session storage (e.g., NextAuth, Chrome storage)
    │ ├── config/ # Environment config & secrets
    ├── presentation/ # User-facing interfaces (UI, API)
    │ ├── api/ # FastAPI routes/controllers
    │ ├── web/ # Next.js components & pages
    │ ├── extension/ # Chrome extension UI & scripts
    │ ├── mobile/ # React Native components
    │ ├── middleware/ # Request/Response middleware
    ├── shared/ # Cross-platform utilities & types
    │ ├── components/ # Shared UI elements (Next.js, React Native)
    │ ├── hooks/ # Reusable hooks (React, Next.js, React Native)
    │ ├── utils/ # Helper functions (server + frontend)
    │ ├── types/ # TypeScript types (backend + frontend)
    ├── tests/ # Unit and integration tests (Jest, Pytest)
    ├── scripts/ # Deployment and automation scripts (Docker, CI/CD)
    └── README.md # Documentation

## Code Syntax, Formatting and Naming Conventions

    - Use the function keyword for pure functions.
    - Avoid unnecessary curly braces in conditionals.
    - Use lowercase with dashes for directories (e.g., components/form-wizard).
    - Use PascalCase for component files (e.g., VisaForm.tsx).
    - Use camelCase for utility files (e.g., formValidator.ts).
    - Use kebab-case for all other file names (file-name.ts).
    - Use camelCase for variables and functions.
    - Use descriptive names (avoid abbreviations).
    - Prefix private members with an underscore (_privateVar).
    - Use PascalCase for classes (e.g., UserModel).
    - Use PascalCase for interfaces without 'I' prefix (e.g., User instead of IUser)
    - Use UPPER_SNAKE_CASE for constants (e.g., API_BASE_URL).
    - Favor named exports for components and utilities.
    - use declarative JSX for readability and maintainability.
    - Follow Prettier and ESLint rules for formatting consistency.

## Always create a .gitignore file containing these files / folders:

# logs

    logs
    *.log
    npm-debug.log*
    yarn-debug.log*
    yarn-error.log*
    pnpm-debug.log*
    lerna-debug.log*
    node_modules
    dist
    dist-ssr
    *.local

# Editor directories and files

    .vscode/*
    !.vscode/extensions.json
    .idea
    .DS_Store
    *.suo
    *.ntvs*
    *.njsproj
    *.sln
    *.sw?

## UI & Styling

    - Use Shadcn UI, Radix, and Tailwind CSS for components and styling.
    - use `npx shadcn@latest add <component-name>` to add new shadcn components
    - Implement responsive design with Tailwind CSS; use a mobile-first approach.
    - When adding a new Shadcn component, also print out the command to add it in the output.
    - Keep component structure flat to improve readability and maintainability.
    - Avoid overriding Tailwind utility classes excessively—prefer composition over specificity.

## Performance Optimization

    - Minimize use client, useEffect, and setState; favor React Server Components (RSC), Use only for Web API access in small components, Avoid for data fetching or state management.
    - Wrap client components in Suspense with a fallback.
    - Use dynamic loading for non-critical components.
    - Optimize images: Use WebP format, Include size data for faster layout rendering, Implement lazy loading.
    - Prefer Edge Functions or Serverless APIs when appropriate for scalability.
    - Use React.memo to optimize re-renders in client components
    - Use Data Access Layer pattern for database access in components
    - Use server actions for data fetching and state management in components
    - Follow Next.js docs for Data Fetching, Rendering, and Routing

## Security

    - Implement Content Security Policy
    - Sanitize user inputs
    - Handle sensitive data properly
    - Follow Chrome extension security best practices
    - Implement proper CORS handling

## Error Handling

    - Write comprehensive tests for all functionalities.
    - Implement proper error boundaries
    - Log errors appropriately for debugging
    - Provide user-friendly error messages
    - Handle network failures gracefully
    - Implement robust error handling mechanisms. For example, in FastAPI, use exception handlers to manage errors gracefully

## Documentation

    - Provide clear and concise documentation for all modules and functions.
    - Use TSDoc for TypeScript documentation and docstrings for Python.
    - Maintain clear README with setup instructions
    - Document API interactions and data flows
    - Keep manifest.json well-documented
    - Don't include comments unless it's for complex logic
    - Document permission requirements
    - Include documentation generation rules

## Development Workflow

    - Follow proper semantic versioning for all projects
    - Implement proper code review process
    - Test in multiple environments
    - Follow semantic versioning for releases
    - Maintain changelog
    - Add PR template requirements
    - Add changelog maintenance guidelines

## Interactive Rules:

    - Automatically suggest in a comment to change the README.md file, If dependencies are updated or critical information should be documented
    - Automatically suggest in a comment for addition of rules in codeGeneration-instructions.md where best practice in used in the code generation
    - Automatically suggest in a comment for changing of rules in codeGeneration-instructions.md where best code generation caused problems and bugs.
    - Automatically suggest in a comment for updating of rules in codeGeneration-instructions.md where if a new coding style is introduced in my codebase.
