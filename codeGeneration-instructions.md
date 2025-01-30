## Instructions for General Code Generation

    - Follow DRY (Don't Repeat Yourself) and KISS (Keep It Simple, Stupid) principles for maintainability.
    - Ensure code readability with consistent indentation, spacing, and meaningful names.
    - Write modular, reusable code to improve flexibility and testability.
    - Implement structured logging to simplify debugging and error tracking.
    - Use error handling and graceful fallbacks to improve reliability and availability.
    - Prioritize security: sanitize inputs, follow least privilege principles, and enforce authentication.
    - Optimize performance by reducing redundant computations and unnecessary API calls.
    - Ensure cross-platform compatibility and avoid framework-specific dependencies when possible.
    - Write comprehensive tests to validate functionality and catch regressions early.
    - Design scalable and efficient architectures to support future growth.

## Preferred Technology Stack and Versions

    - Generate code using ONLY the following technologies and their specified versions:

**Frontend:**

    - Next.js:Version 13.4.12
    - Tailwind CSS:Version 3.3.2
    - React Native:Version 0.72.3

**Backend:**

    - FastAPI:Version 0.100.0

**Database:**

    - PostgreSQL:Version 15.3

**ORM:**

    - Prisma:Version 4.15.0

**Authentication:**

    - NextAuth.js (Auth.js):Version 4.22.1

**Testing:**

    - Jest:Version 29.6.1
    - React Testing Library:Version 14.0.0
    - Pytest:Version 7.4.0

**Logging and Monitoring:**

    - Sentry SDK for JavaScript:Version 7.59.0
    - Sentry SDK for Python:Version 1.29.2

**Containerization and Deployment:**

    - Docker:Version 24.0.5
    - Coolify:Version 3.8.0

## Instructions for Next.js Code Generation

    - Use functional components and React hooks for clean, reusable code.
    - Optimize state management for smooth page transitions and user interactions.

## Instructions for Tailwind CSS Code Generation

    - Keep utility classes organized and meaningful for better maintainability.
    - Avoid excessive nesting to reduce CSS bloat and improve performance.
    - Prefer responsive, reusable styles over inline custom styles.

## Instructions for React Native Code Generation

    - Prioritize component reusability and use TypeScript for type safety.
    - Minimize state usage to avoid performance bottlenecks.
    - Maintain a clear project structure for easier testing and debugging.
    - Optimize network requests using caching and background sync where applicable.

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

## Code Formatting and Naming Conventions

    General Syntax and Formatting
    - Use the function keyword for pure functions.
    - Avoid unnecessary curly braces in conditionals.
    File and Directory Naming
    - Use lowercase with dashes for directories (e.g., components/form-wizard).
    - Use PascalCase for component files (e.g., VisaForm.tsx).
    - Use camelCase for utility files (e.g., formValidator.ts).
    - Use kebab-case for all other file names (file-name.ts).
    Variable and Function Naming
    - Use camelCase for variables and functions.
    - Use descriptive names (avoid abbreviations).
    - Prefix private members with an underscore (_privateVar).
    Class and Interface Naming
    - Use PascalCase for classes (e.g., UserModel).
    - Use PascalCase with an 'I' prefix for interfaces (e.g., IUser).
    Constants
    - Use UPPER_SNAKE_CASE for constants (e.g., API_BASE_URL).
    Exports and Imports
    - Favor named exports for components and utilities.

## Coding Conventions and Best Practices:

    - Code Consistency:Ensure that all code adheres to the specified versions of the technologies listed above to maintain consistency across projects.
    - Error Handling:Implement robust error handling mechanisms. For example, in FastAPI, use exception handlers to manage errors gracefully.
    - Testing:Write comprehensive tests for all functionalities. Utilize the specified testing frameworks to ensure code reliability.
    - Logging:Integrate logging using the specified Sentry SDKs to monitor and debug applications effectively.
    - Documentation:Provide clear and concise documentation for all modules and functions. Use docstrings in Python and JSDoc in JavaScript/TypeScript where applicable.
    - Code Formatting:Adhere to standard code formatting guidelines. For instance, use Prettier for JavaScript/TypeScript and Black for Python to maintain uniformity.
    - Version Control:Follow semantic versioning for all projects and ensure that version numbers are updated appropriately with each release.
