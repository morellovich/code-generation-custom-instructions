# Common Rules for All Roocode Modes

version: 1.0.0

## Core Principles

- Follow DRY (Don't Repeat Yourself) and KISS (Keep It Simple, Stupid) principles for maintainability.
- Ensure code readability with consistent indentation, spacing, and meaningful names.
- Write modular, reusable code to improve flexibility and testability.
- Prefer iteration and modularization over code duplication.
- Take a security-first approach in all considerations.
- Prioritize performance in all design and code changes.
- Implement robust error handling and graceful fallbacks.
- Follow modular design principles.
- Ensure version compatibility across the stack.
- Avoid magic numbers by using named constants.
- Consider and handle edge cases thoroughly.
- Use assertions to validate assumptions where appropriate.

## Project Structure

- Adhere strictly to the following folder structure:
  \`\`\`
  src/
  ├── core/ # Business logic (reusable across backend/frontend)
  │ ├── domain/ # Business entities & validation rules
  │ ├── usecases/ # Application logic & services
  │ └── interfaces/ # Abstract interfaces for business rules
  ├── infrastructure/ # System-level implementations
  │ ├── database/ # Database implementations (PostgreSQL, Prisma)
  │ ├── external/ # External API integrations (e.g., Auth, Sentry)
  │ ├── storage/ # Storage solutions (e.g., file, session)
  │ └── config/ # Configuration files (environment variables, secrets)
  ├── presentation/ # User-facing interfaces (UI, API)
  │ ├── api/ # FastAPI routes/controllers
  │ ├── web/ # Next.js components & pages
  │ ├── extension/ # Chrome extension UI & scripts
  │ ├── mobile/ # React Native components
  │ └── middleware/ # Middleware for request/response handling
  ├── shared/ # Shared utilities & types across platforms
  │ ├── components/ # Shared UI components (Next.js, React Native)
  │ ├── hooks/ # Reusable hooks (React, Next.js, React Native)
  │ ├── utils/ # Utility functions (server + frontend)
  │ └── types/ # TypeScript types (backend + frontend)
  ├── tests/ # Unit and integration tests (Jest, Pytest)
  ├── scripts/ # Deployment and automation scripts (Docker, CI/CD)
  ├── migrations/ # Database migration files (Prisma)
  ├── docs/ # Project documentation
  │ ├── architecture.md # Architecture overview
  │ ├── api_reference.md # API reference documentation
  │ └── user_guide.md # User guide documentation
  └── coding_rules/ # Coding standards and guidelines (ESLint, Prettier)
  ├── eslint.md
  ├── prettier.md
  └── conventions.md
  └── README.md # Project documentation
  \`\`\`

## Naming Conventions

- **Directories**: lowercase-with-dashes (e.g., `components/form-wizard`)
- **Component Files**: PascalCase (e.g., `VisaForm.tsx`)
- **Utility Files**: camelCase (e.g., `formValidator.ts`)
- **Other Files**: kebab-case (e.g., `api-endpoints.ts`)
- **Variables & Functions**: camelCase (e.g., `getUserProfile`)
- **Private Members**: Prefix with underscore (`_privateVar`, `_calculateTotal`)
- **Classes**: PascalCase (e.g., `UserModel`) - _Use sparingly, prefer functions._
- **Interfaces**: PascalCase without 'I' prefix (e.g., `User` instead of `IUser`)
- **Constants**: UPPER_SNAKE_CASE (e.g., `API_BASE_URL`, `MAX_RETRIES`)

## Technology Stack & Versions

_You are an expert senior developer in these technologies._

- **Frontend:**
  - Next.js: 14.x (latest stable)
  - React: 18.x (latest stable)
  - Tailwind CSS: 3.x (latest stable)
  - React Native: (Specify version if used)
- **Backend:**
  - FastAPI: (Specify version, e.g., 0.104.1+)
  - Python: 3.10+
- **Database:**
  - PostgreSQL: 15+
- **ORM:**
  - Prisma: 5.x (latest stable)
- **Authentication:**
  - NextAuth.js (Auth.js): 4.x (latest stable)
- **Testing:**
  - Jest: 29.x
  - React Testing Library: 14.x
  - Pytest: 7.x
  - Playwright: 1.x (latest stable)
- **Logging & Monitoring:**
  - Sentry SDK (JS & Python): Latest stable versions
- **Containerization & Deployment:**
  - Docker: Latest stable
  - Coolify: (Specify version/setup if used)
- **Linting/Formatting:**
  - ESLint: (Specify config)
  - Prettier: (Specify config)

## Commit Message Format (Conventional Commits)

- **Structure**: `<type>(<scope>): <subject>`
  - `<type>`: `fix`, `feat`, `perf`, `docs`, `style`, `refactor`, `test`, `chore`, `build`, `ci`
  - `<scope>`: Optional, indicates the part of the codebase affected (e.g., `auth`, `ui`, `api`).
  - `<subject>`: Concise description in present tense, lowercase start, no period at end.
- **Body**: Optional, provide more context after a blank line.
- **Footer**: Optional, for `BREAKING CHANGE:` notes or issue references (`Refs: #123`).
- **Example**: `feat(api): add user profile endpoint`
- **Rules**:
  - Use lowercase for the entire message.
  - Reference issue numbers when applicable.
  - Include `BREAKING CHANGE:` in the footer for incompatible changes.

## Development Workflow

- Make changes file by file to isolate errors.
- Preserve existing code structures unless refactoring is the goal.
- Provide all edits for a single file in one chunk/diff.
- Always look for existing code to iterate on before creating new code.
- Do not change established patterns without strong justification.
- Write code considering different environments (dev, test, prod).
- Only make changes that are requested or clearly necessary for the task.
- When fixing issues, exhaust options with the existing implementation first.
- Keep files concise; refactor files exceeding ~300 lines.
- Focus on code areas relevant to the task; avoid unrelated changes.
- Consider potential impacts on other parts of the codebase.
- After making changes, always restart relevant servers/processes for testing.
- Kill existing related servers before starting new ones to avoid conflicts.

## Communication Guidelines (for AI interaction)

- No apologies needed.
- No "understanding" feedback (e.g., "Okay, I understand").
- No unnecessary summaries of changes already visible.
- No suggestions for whitespace-only changes.
- No invention of changes beyond the request.
- No unnecessary confirmation requests for visible context.

## .gitignore Defaults

- Always include standard ignores for logs, dependencies, build artifacts, local configs, and editor files.
  \`\`\`

# Logs

logs
_.log
npm-debug.log_
yarn-debug.log*
yarn-error.log*
pnpm-debug.log*
lerna-debug.log*

# Dependencies

node_modules
.pnp
.pnp.js

# Build artifacts

dist
dist-ssr
build
.next
out

# Local configs & environment variables

_.local
.env.local
.env._.local
!.env.example

# Editor directories and files

.vscode/_
!.vscode/extensions.json
!.vscode/settings.json
.idea
_.suo
_.ntvs_
_.njsproj
_.sln
\*.sw?

# OS generated files

.DS_Store
Thumbs.db
\`\`\`
