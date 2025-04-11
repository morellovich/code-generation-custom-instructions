romo9889: @workspace I want to create custom instructions to Roo Cline that I'm also using to generate code. I want you to dig deep into all my GitHub-Copilot's custom instructions in the folder (.github) and the instructions in the links below to perform the following:
A- https://docs.roocode.com/advanced-usage/custom-instructions/
B- https://docs.roocode.com/advanced-usage/custom-modes/

1- Create custum instructions files for each of the standard Roo Cline modes (Code, Architect, ASk, Debug) using this naming scheme {.clinerules-[mode]} e.g., .clinerules-code.

2- These four files should cover ALL custom instructions from my GitHub-Copilot's custom instructions in the folder (.github) and NEVER forget any single one of them.

3- The resullt should be AT LEAST four .clinerules file for each modes of Roo Cline

4- Scan for any Conflicting instructions, or instructions that might interduce bugs and errors later on.

5- Make suggestion to Create OR Modoify Roo Cline modes based on my needs as a web developer and data analyst. Following ONLY best practices.

Workspace: Collecting workspace informationI'll create custom instruction files for Roo Cline based on your GitHub Copilot custom instructions. After analyzing your files, I'll create the four standard mode files and make suggestions for additional modes that might benefit you.

## 1. Standard Mode Files

Let me create the four standard mode files for Roo Cline:

### .clinerules-code

```markdown
# Roo Cline Code Mode Instructions

## General Code Generation

- Follow DRY (Don't Repeat Yourself) and KISS (Keep It Simple, Stupid) principles
- Ensure code readability with consistent indentation, spacing, and meaningful names
- Write modular, reusable code to improve flexibility and testability
- Use functional and declarative programming patterns; avoid classes when possible
- Prefer iteration and modularization over code duplication
- Use explicit return types for all functions
- Use absolute imports for all files @/...

## Technology Stack

**Frontend:**

- Next.js (latest stable)
- Tailwind CSS
- React Native

**Backend:**

- FastAPI

**Database:**

- PostgreSQL
- Prisma ORM

**Authentication:**

- NextAuth.js (Auth.js)

**Testing:**

- Jest (v29.6.1)
- React Testing Library (v14.0.0)
- Pytest (v7.4.0)

**Monitoring:**

- Sentry SDK

**Deployment:**

- Docker
- Coolify

## Folder Structure

Follow this project structure:
```

src/
├── core/ # Business logic
│ ├── domain/ # Business entities & validation rules
│ ├── usecases/ # Application logic & services
│ ├── interfaces/ # Abstract interfaces for business rules
├── infrastructure/ # System-level implementations
│ ├── database/ # PostgreSQL & Prisma
│ ├── external/ # API integrations
│ ├── storage/ # File & session storage
│ ├── config/ # Environment config & secrets
├── presentation/ # User-facing interfaces
│ ├── api/ # FastAPI routes/controllers
│ ├── web/ # Next.js components & pages
│ ├── extension/ # Chrome extension UI
│ ├── mobile/ # React Native components
│ ├── middleware/ # Request/Response middleware
├── shared/ # Cross-platform utilities
│ ├── components/ # Shared UI elements
│ ├── hooks/ # Reusable hooks
│ ├── utils/ # Helper functions
│ ├── types/ # TypeScript types
├── tests/ # Unit and integration tests
├── scripts/ # Deployment and automation scripts

```

## Naming Conventions

- Use lowercase with dashes for directories (e.g., `form-wizard/`)
- Use PascalCase for component files (e.g., `UserForm.tsx`)
- Use camelCase for utility files (e.g., `formValidator.ts`)
- Use kebab-case for all other files (e.g., `api-endpoints.ts`)
- Use camelCase for variables and functions
- Use descriptive names and avoid abbreviations
- Prefix private members with underscore (`_privateVar`)
- Use PascalCase for interfaces without 'I' prefix (`User` not `IUser`)
- Use UPPER_SNAKE_CASE for constants (e.g., `API_BASE_URL`)

## React/Next.js Best Practices

- Use functional components and React hooks instead of class components
- Use Server Components by default
- Implement React Server Actions instead of client-side API calls
- Use route handlers instead of API routes when possible
- Prefer interfaces over types
- Avoid enums; use maps instead
- Use try/catch only for external API calls, file operations, database queries, browser API interactions
- Wrap client components in Suspense with a fallback
- Use React.memo for client components that re-render frequently

## UI & Styling

- Use Shadcn UI and Tailwind CSS for components and styling
- Implement responsive design with a mobile-first approach
- Keep utility classes organized for better maintainability
- Avoid excessive nesting to reduce CSS bloat
- Prefer composition over specificity with Tailwind classes

## Performance Optimization

- Minimize `use client`, useEffect, and setState
- Use dynamic loading for non-critical components
- Optimize images using WebP format with size data
- Use Data Access Layer pattern for database access
- Use server actions for data fetching and state management

## Error Handling

- Implement proper error boundaries
- Log errors appropriately for debugging
- Provide user-friendly error messages
- Handle network failures gracefully
- Use structured error handling for endpoints
```

### .clinerules-architect

```markdown
# Roo Cline Architect Mode Instructions

## Architecture Goals

- Design scalable and efficient architectures to support future growth
- Create separate files for framework-specific rules
- Maintain a single source of truth for common rules
- Include decision trees for technical choices
- Create an index file linking to specific instruction sets
- Use a hierarchical structure for related rules

## Technology Selection

**Frontend:**

- React for server-rendered React applications
- React Native for mobile applications
- Tailwind CSS for styling

**Backend:**

- FastAPI for high-performance API development
- PostgreSQL for relational data storage
- Prisma as ORM for type-safe database access

**Authentication:**

- NextAuth.js with support for multiple providers

**Monitoring & Logging:**

- Sentry SDK for error tracking and performance monitoring
- Structured logging throughout the application

**Testing:**

- Jest and React Testing Library for frontend
- Playwright for E2E testing
- Pytest for backend

## Project Structure

Structure your project following clean architecture principles:
```

src/
├── core/ # Business logic (reusable across backend/frontend)
│ ├── domain/ # Business entities & validation rules
│ ├── usecases/ # Application logic & services
│ ├── interfaces/ # Abstract interfaces for business rules
├── infrastructure/ # System-level implementations
│ ├── database/ # PostgreSQL & Prisma implementations
│ ├── external/ # API integrations (e.g., Auth, Sentry)
│ ├── storage/ # File & session storage (e.g., NextAuth)
│ ├── config/ # Environment config & secrets
├── presentation/ # User-facing interfaces
│ ├── api/ # FastAPI routes/controllers
│ ├── web/ # Next.js components & pages
│ ├── extension/ # Chrome extension UI & scripts
│ ├── mobile/ # React Native components
│ ├── middleware/ # Request/Response middleware
├── shared/ # Cross-platform utilities & types
├── tests/ # Unit and integration tests
├── scripts/ # Deployment and automation scripts

```

## API Design

- Follow REST principles with consistent resource naming
- Implement proper versioning strategy
- Use OpenAPI/Swagger for API documentation
- Design for backward compatibility
- Enable proper CORS handling

## Database Design

- Follow normalization principles
- Use indexes for query optimization
- Implement proper transaction handling
- Use migrations for schema changes
- Apply proper indexing strategies for performance

## Authentication & Security

- Implement CSRF protection and secure cookie settings
- Support for OAuth, JWT, and multi-factor authentication (MFA)
- Implement content security policy
- Sanitize all user inputs
- Follow least privilege principles
- Enforce role-based access control (RBAC)

## Performance Considerations

- Use Edge Runtime when appropriate
- Implement streaming and progressive rendering
- Set up proper caching strategies
- Use server components where possible
- Optimize for Core Web Vitals metrics
- Implement proper accessibility requirements

## Testing Architecture

- Unit tests for domain logic
- Integration tests for API endpoints
- E2E tests for critical user flows
- Performance testing for key operations
- Cross-browser compatibility testing

## Deployment Architecture

- Use optimized Docker images with multi-stage builds
- Implement health checks and restart policies
- Define proper environment variables
- Set up CI/CD pipelines
- Implement automated backup strategies
```

### .clinerules-ask

# Roo Cline Ask Mode Instructions

## Response Guidelines

- Provide clear, concise responses focused on requested information
- When discussing code, follow the established conventions and best practices
- Reference appropriate documentation when suggesting technologies
- Prioritize security, performance, and accessibility in recommendations
- Explain technical concepts clearly without unnecessary jargon

## Technology Stack Knowledge

**Frontend:**

- Next.js (latest stable version)
- React and React Native
- Tailwind CSS with Shadcn UI components
- Server Components and Client Components
- React Server Actions

**Backend:**

- FastAPI for Python-based APIs
- PostgreSQL for database
- Prisma as ORM
- NextAuth.js for authentication

**Testing:**

- Jest (v29.6.1)
- React Testing Library (v14.0.0)
- Pytest (v7.4.0)
- Playwright for E2E testing

**DevOps:**

- Docker containerization
- Coolify for deployment
- GitHub Actions for CI/CD

## Coding Standards

When discussing code samples:

- Use functional components and hooks for React
- Prefer interfaces over types in TypeScript
- Avoid enums; recommend maps instead
- Follow naming conventions:
  - PascalCase for components and interfaces
  - camelCase for variables and functions
  - UPPER_SNAKE_CASE for constants

## Project Structure Knowledge

Refer to this project structure in discussions:

```

src/
├── core/ # Business logic
├── infrastructure/ # System-level implementations
├── presentation/ # User-facing interfaces
├── shared/ # Cross-platform utilities
├── tests/ # Tests
├── scripts/ # Deployment scripts

```

## Security Focus

Always emphasize:

- Input sanitization
- Authentication and authorization
- Content Security Policy implementation
- Proper handling of sensitive data
- CORS configuration
- Error handling without exposing sensitive details

## Performance Considerations

When answering performance questions:

- Recommend server components over client components when possible
- Suggest data fetching patterns using React Server Actions
- Emphasize image optimization techniques
- Discuss code splitting and dynamic imports
- Mention Core Web Vitals metrics importance

## Documentation Guidance

When discussing documentation:

- Recommend TSDoc for TypeScript
- Suggest Python docstrings
- Emphasize clear README with setup instructions
- Mention the importance of API documentation
- Recommend documenting permissions requirements

````

### .clinerules-debug

```markdown
# Roo Cline Debug Mode Instructions

## Debugging Approach

- Analyze the problem systematically and step by step
- Check for syntax errors first, then logical errors
- Consider edge cases and unexpected inputs
- Look for common pitfalls related to the specific technology
- Suggest clear, actionable solutions with examples

## Error Handling Best Practices

- Implement proper error boundaries in React applications
- Use try/catch blocks appropriately for:
  - External API calls
  - File operations
  - Database queries
  - Browser API interactions
- Use structured logging for better debugging
- Provide user-friendly error messages
- Implement graceful fallbacks for failures

## Common Issues to Check

### Next.js / React Issues

- Check for React key errors in lists
- Verify proper use of useState and useEffect hooks
- Check for memory leaks in useEffect (missing cleanup)
- Verify proper use of Server Components vs Client Components
- Look for data fetching issues with Server Actions

### TypeScript Issues

- Check for type mismatches and null/undefined handling
- Verify proper interface definitions
- Look for incorrect type assertions

### API / Backend Issues

- Check for CORS configuration issues
- Verify proper error handling in async functions
- Check for database connection issues
- Verify proper validation of input data

### Database Issues

- Look for transaction handling problems
- Check for missing indexes causing performance issues
- Verify proper foreign key constraints

### Authentication Issues

- Check for proper session handling
- Verify CSRF protection implementation
- Look for secure cookie settings

## Testing for Bugs

- Suggest unit tests to verify fixes
- Recommend E2E tests for critical flows
- Emphasize test-driven development for future prevention

## Monitoring and Logging

- Implement Sentry SDK for error tracking
- Use breadcrumbs and user context for detailed error reports
- Ensure sensitive data is masked in logs
- Suggest structured logging patterns

## Debugging Tools

- Recommend browser DevTools for frontend issues
- Suggest server-side logging for backend problems
- Recommend using Playwright for debugging UI issues
- Suggest database query analyzers for SQL problems

## Performance Debugging

- Look for unnecessary re-renders in React
- Check for N+1 query problems in database access
- Verify proper image optimization
- Look for memory leaks in long-running processes
````

## 2. Conflicts and Issues Found

After analyzing your instructions, I identified several conflicts and potential issues:

1. **Architecture Conflicts**:

   - The instructions say "avoid classes when possible" but also specify "Use PascalCase for classes"
   - This creates confusion about whether classes should be used at all

2. **Next.js Server Components vs. React Native**:

   - Instructions mention Server Components and React Native together, but React Native doesn't support Server Components
   - This could lead to confusion when developing for both platforms

3. **Testing Framework Inconsistencies**:

   - The instructions mention both Playwright and Jest/React Testing Library without clear boundaries
   - The test file location mentions both `/tests` and `src/lib/migrations` for test-related files

4. **Chrome Extension vs. Web App Architecture**:

   - The folder structure tries to accommodate both Chrome extensions and web apps
   - This creates unnecessary complexity if you're only building one type of application

5. **Missing Version Information**:
   - Many technologies don't have specific versions listed (Next.js, Tailwind, FastAPI)
   - This could lead to compatibility issues when specific features are used

## 3. Suggested Additional Roo Cline Modes

Based on your needs as a web developer and data analyst, I recommend creating these additional custom modes:

### .clinerules-data

```markdown
# Roo Cline Data Mode Instructions

## Data Analysis Focus

- Prioritize data integrity and validation
- Use strong typing for data models
- Implement proper error handling for data processing
- Consider performance implications for large datasets
- Use appropriate visualization techniques

## Database Design

- Follow normalization principles for PostgreSQL
- Use indexes strategically for query optimization
- Implement proper constraint management
- Use transactions for data consistency
- Apply indexing strategies based on query patterns

## Data Processing Libraries

- Use pandas and numpy for Python data processing
- Implement proper data cleaning techniques
- Consider streaming processing for large datasets
- Use appropriate aggregation methods

## Data Visualization

- Use appropriate charts based on data characteristics
- Ensure accessibility in visualizations
- Implement responsive design for dashboards
- Consider performance for large dataset visualizations

## SQL Best Practices

- Write optimized queries with proper JOINs
- Use CTEs for complex queries instead of nested subqueries
- Implement pagination for large result sets
- Use parameterized queries to prevent SQL injection
- Consider query performance and execution plans

## Prisma Data Access

- Use Prisma for type-safe database access
- Implement proper transaction handling
- Use include and select to optimize data fetching
- Implement proper error handling for database operations
- Use the Data Access Layer pattern for database interactions

## Data Security

- Implement proper data encryption
- Handle sensitive data according to regulations
- Implement proper authentication and authorization
- Use data masking for sensitive information
- Implement audit logging for data modifications
```

### .clinerules-fullstack

```markdown
# Roo Cline Fullstack Mode Instructions

## Full Stack Development Focus

- Ensure consistency between frontend and backend
- Use type sharing between client and server
- Implement proper error handling across the stack
- Consider end-to-end testing for critical flows
- Optimize data transfer between layers

## Frontend Development

- Use Next.js Server Components by default
- Implement React Server Actions for data mutations
- Use Tailwind CSS with Shadcn UI for components
- Optimize for Core Web Vitals
- Implement proper accessibility standards

## Backend Development

- Use FastAPI for high-performance APIs
- Implement proper validation with Pydantic
- Use async functions for non-blocking operations
- Generate OpenAPI documentation
- Implement proper error handling

## Database Integration

- Use Prisma for type-safe database access
- Implement proper migration management
- Use transactions for data consistency
- Optimize queries for performance
- Implement proper connection pooling

## Authentication Flow

- Use NextAuth.js for authentication
- Implement proper session management
- Use secure cookies and CSRF protection
- Support multiple auth providers
- Implement role-based access control

## API Development

- Design RESTful APIs with proper resource naming
- Implement versioning strategy
- Use proper HTTP status codes
- Document APIs with OpenAPI/Swagger
- Implement proper rate limiting

## State Management

- Use React Context sparingly
- Prefer Server Components and Server Actions
- Implement optimistic updates for better UX
- Handle loading and error states properly
- Use client-side state only when necessary
```

## 4. Recommendations for Improvement

1. **Resolve Architectural Conflicts**:

   - Clarify the stance on classes vs. functional programming
   - Separate React Native and Web instructions more clearly
   - Be more specific about when to use what pattern

2. **Simplify and Modularize Instructions**:

   - Create an index file that references specific instruction sets
   - Use more hierarchical structure to reduce repetition
   - Separate framework-specific rules into dedicated files

3. **Improve Version Management**:

   - Add specific compatible versions for all technologies
   - Include upgrade paths and compatibility notes
   - Document version-specific features and limitations

4. **Enhance Testing Instructions**:

   - Add specific code coverage requirements
   - Clarify testing strategies for different parts of the application
   - Provide more specific E2E testing scenarios

5. **Add Accessibility Requirements**:

   - Include WCAG compliance standards
   - Specify accessibility testing tools
   - Add guidelines for keyboard navigation and screen readers

6. **Enhance Security Guidelines**:
   - Add more specific content security policy examples
   - Include OWASP top 10 protections
   - Add guidelines for secure authentication implementation

These custom instruction files should help you use Roo Cline more effectively while maintaining consistency with your existing GitHub Copilot instructions. The additional specialized modes will enhance your productivity for specific types of development work.

romo9889: @workspace
1- Does it make scence to repeat these rule across multiple files as you did? This way the files are too long (I think) and complicated, will this cause any issues? also will this increase the API usage and cost more?

2- Why creating a separate FullStack mode if it's already covered (logically) in all modes?

3- base on you Recommendations for Improvement, make a list of clear instructions that ONLY follow best practices to add to each file of the already 5 existing files in .github and also .clinerules files, suggest additions OR removals for each one of the files.

Workspace: Collecting workspace information# Analysis of Rule Distribution and Mode Structure

## 1. Rule Repetition Analysis

No, repeating all rules across multiple files isn't ideal for several reasons:

1. **Token/Cost Efficiency**: Longer files with repeated content increase API token usage and costs when sent to the model.
2. **Maintenance Overhead**: When rules change, you need to update them in multiple places.
3. **Cognitive Load**: Longer files are harder to read and maintain.
4. **Prompt Clarity**: Models perform better with concise, focused instructions.

A better approach is to create a modular structure with:

- Base rules in a common file
- Mode-specific rules in separate files
- Cross-references between files rather than repetition

## 2. FullStack Mode Analysis

The FullStack mode doesn't need to be separate because:

1. The standard modes already cover the end-to-end development workflow
2. It contains significant overlap with Code and Architect modes
3. Having too many modes creates decision fatigue

Instead, it's better to ensure that Code and Architect modes properly handle fullstack scenarios by including appropriate cross-layer considerations.

## 3. Recommended Changes to Instruction Files

### Changes for .github Files

#### codeGeneration-instructions.md

```markdown
# Additions

- Create a Table of Contents with links to each section
- Add specific version numbers for all technologies
- Add a section on compatibility between frameworks
- Include decision trees for technology selection

# Removals

- Remove repetitive error handling guidance across multiple sections
- Remove conflicting statements about class usage
- Consolidate similar instructions scattered across sections
```

#### testGeneration-instructions.md

```markdown
# Additions

- Add specific code coverage requirements (e.g., 80% minimum)
- Include performance testing metrics and thresholds
- Add guidelines for mocking external dependencies

# Removals

- Remove database migration references from testing file (keep in DB section)
- Remove redundant testing setups between frameworks
```

#### reviewSelection-instructions.md

```markdown
# Additions

- Add specific security review checklist (OWASP Top 10)
- Include accessibility review guidelines (WCAG)
- Add performance review metrics

# Removals

- Remove vague language about "meaningful improvements"
```

#### commitMessageGeneration-instructions.md

```markdown
# Additions

- Add examples for each commit type
- Include scope definition guidelines
- Add breaking change notation

# Removals

- Fix spelling error in "Insttructions" title
- Remove redundancy in the commit message guidelines
```

#### copilot-instructions.md

```markdown
# Additions

- Replace placeholder project context with actual project description
- Add specific examples for each development phase
- Include environment setup instructions

# Removals

- Remove placeholder brackets and text
- Remove redundant analysis section at the end
```

### Changes for .clinerules Files

#### .clinerules-code

```markdown
# Additions

- Add specific patterns and anti-patterns with examples
- Include specific library version numbers
- Add a troubleshooting section for common errors

# Removals

- Remove architecture guidance (belongs in architect mode)
- Remove general principles that should be in a common file
- Remove project structure details (reference architect mode)
```

#### .clinerules-architect

```markdown
# Additions

- Add system design patterns with examples
- Include performance benchmarks and optimization techniques
- Add migration strategies for legacy systems

# Removals

- Remove code-level implementation details
- Remove debugging instructions (belongs in debug mode)
```

#### .clinerules-ask

```markdown
# Additions

- Add context gathering prompts
- Include reference documentation links
- Add decision tree for technology recommendations

# Removals

- Remove implementation details
- Remove debugging instructions
```

#### .clinerules-debug

```markdown
# Additions

- Add environment-specific debugging strategies
- Include common error message interpretation guide
- Add performance profiling techniques

# Removals

- Remove architecture-related content
- Remove general coding principles (reference code mode)
```

#### .clinerules-data

```markdown
# Additions

- Add specific data processing libraries and versions
- Include data visualization best practices
- Add data validation techniques

# Removals

- Remove general database setup (reference from architect mode)
```

## General Recommendation

Create a `.clinerules-common` file with shared principles and have each mode-specific file include only mode-relevant instructions with references to the common file. This would significantly reduce duplication while maintaining clarity.

romo9889: @workspace

1- Based of these suggestions, recreate each one of the .clinerules files from scratch, make the instructions full, clear and spicific, not to generic as you just provided. I want concrete rules to the logic behind them

2- Based of these suggestions, make a list of full, clear and spicific rules to add for each one of the 5 files in .github

3- Based of these suggestions, specify exactly which rules in which lines in which file to be removed in or each one of the 5 files in .github

Workspace: Collecting workspace information# 1. Recreated .clinerules Files

## .clinerules-common

```markdown
# Common Rules for All Modes

version: 1.0.0

## Project Structure

- Follow the standard folder structure exactly:
```

src/
├── core/ # Business logic
│ ├── domain/ # Entities & validation rules
│ ├── usecases/ # Application logic
│ ├── interfaces/ # Abstract interfaces
├── infrastructure/ # System implementations
│ ├── database/ # DB implementations
│ ├── external/ # API integrations
│ ├── storage/ # Storage implementations
│ ├── config/ # Environment config
├── presentation/ # User interfaces
│ ├── api/ # API controllers
│ ├── web/ # Web components
│ ├── extension/ # Extension UI
│ ├── mobile/ # Mobile components
│ ├── middleware/ # Request middleware
├── shared/ # Cross-platform utils
├── tests/ # Tests
├── scripts/ # Build scripts

```

## Naming Conventions
- Directories: lowercase-with-dashes (e.g., `user-profiles/`)
- Component files: PascalCase.tsx (e.g., `UserProfile.tsx`)
- Utility files: camelCase.ts (e.g., `formatDate.ts`)
- Other files: kebab-case.ts (e.g., `api-endpoints.ts`)
- Variables/functions: camelCase (e.g., `getUserData()`)
- Private members: underscore prefix (e.g., `_privateMethod()`)
- Constants: UPPER_SNAKE_CASE (e.g., `MAX_RETRY_COUNT`)
- Interfaces: PascalCase without 'I' prefix (e.g., `User` not `IUser`)

## Technology Versions
- Next.js: 14.0.3
- React: 18.2.0
- TypeScript: 5.2.2
- Node.js: 20.9.0
- FastAPI: 0.104.1
- PostgreSQL: 15.4
- Prisma: 5.4.2
- NextAuth.js: 4.24.5
- Jest: 29.7.0
- React Testing Library: 14.1.2
- Pytest: 7.4.3
- Sentry SDK (JS): 7.80.0
- Sentry SDK (Python): 1.32.0
- Docker: 24.0.6
- Tailwind CSS: 3.3.5
```

## .clinerules-code

```markdown
# Code Mode Rules

version: 1.0.0
import: .clinerules-common

## JavaScript/TypeScript

- Use functional components with hooks instead of class components
- Use Server Components by default, only use "use client" when absolutely necessary
- Use React Server Actions for data mutations (form submissions, state updates)
- Avoid class inheritance; prefer composition
- Use explicit return types for all functions
- Use interfaces over types for object shapes
- Use const assertions for literal values (as const)
- Use optional chaining (?.) and nullish coalescing (??) operators
- Replace enum usage with union types or const objects with as const
- Use mapped types for related values
- Use try/catch ONLY for:
  - External API calls
  - File system operations
  - Database queries
  - Browser API interactions

## Next.js Specific

- Use the App Router pattern (/app directory structure)
- Use route handlers instead of API routes when possible
- Use Suspense for loading states
- Set proper caching headers for static assets
- Implement image optimization with the next/image component
- Use metadata API for SEO optimization
- Use dynamic imports for code splitting
- Use server actions for form submissions
- Implement proper error boundaries with error.tsx

## React Patterns

- Use React.memo() only for frequently re-rendered components with expensive renders
- Use useCallback() for functions passed as props to memoized child components
- Use useMemo() only for expensive computations
- Always clean up event listeners and subscriptions in useEffect
- Prefer controlled components over uncontrolled components
- Use React.Fragment instead of div when no element is needed

## State Management

- Use React state for simple component-level state
- Use React Context only for theme, auth, and app-wide preferences
- Use Server Components and Server Actions for most data fetching and state management
- Implement optimistic updates for better user experience
- Separate read operations from write operations

## Performance

- Use <Image> component for all images with proper sizes and formats
- Implement proper lazy loading for below-the-fold content
- Minimize client-side JavaScript with Server Components
- Use Edge Functions for API routes that need global low latency
- Keep bundle size small with proper code splitting
- Implement skeleton loading states for better user experience
- Use React.memo for expensive components that render frequently
```

## .clinerules-architect

```markdown
# Architect Mode Rules

version: 1.0.0
import: .clinerules-common

## System Design Patterns

- Use Domain-Driven Design principles for complex domains
- Implement Clean Architecture with clear separation of concerns:
  - Domain layer: Business logic, entities, validation rules
  - Application layer: Use cases, services, orchestration
  - Interface layer: Controllers, presenters, gateways
  - Infrastructure layer: DB, external services, storage
- Follow SOLID principles:
  - Single Responsibility: One reason to change
  - Open-Closed: Open for extension, closed for modification
  - Liskov Substitution: Subtypes must be substitutable for base types
  - Interface Segregation: Many specific interfaces better than one general
  - Dependency Inversion: Depend on abstractions, not concretions

## Database Design

- Normalize database to at least 3NF for most tables
- Denormalize only when performance requirements justify it
- Use foreign keys to maintain referential integrity
- Implement composite indexes for multi-column queries
- Use appropriate column types (e.g., uuid for IDs, text for variable strings)
- Implement proper constraints (NOT NULL, UNIQUE, CHECK)
- Add proper timestamps (created_at, updated_at) to all tables
- Use enums sparingly, prefer lookup tables for extensibility
- Implement soft deletes for important data (deleted_at timestamp)
- Use connection pooling with appropriate pool size

## API Design

- Design RESTful APIs with consistent resource naming
- Implement proper versioning (URI versioning with /v1/resource)
- Use appropriate HTTP methods (GET, POST, PUT, PATCH, DELETE)
- Return appropriate status codes (200, 201, 400, 401, 403, 404, 500)
- Implement proper validation with detailed error messages
- Include pagination, filtering, and sorting for collection endpoints
- Implement rate limiting for public APIs
- Use JWT for stateless authentication
- Document APIs with OpenAPI/Swagger
- Implement consistent error responses

## Security Architecture

- Implement proper authentication and authorization
- Store passwords with strong hashing (bcrypt/Argon2)
- Implement CSRF protection for all forms
- Use HTTP-only cookies for sensitive data
- Implement proper Content Security Policy
- Use parameterized queries for database access
- Sanitize all user inputs
- Implement proper CORS configuration
- Use HTTPS for all communications
- Implement rate limiting to prevent brute force attacks

## Scalability Patterns

- Implement caching at multiple levels:
  - Browser caching with proper cache headers
  - CDN caching for static assets
  - Application-level caching for frequent queries
  - Database query caching
- Use read replicas for read-heavy workloads
- Implement database sharding for very large datasets
- Use message queues for asynchronous processing
- Implement proper connection pooling
- Design for horizontal scalability
```

## .clinerules-ask

```markdown
# Ask Mode Rules

version: 1.0.0
import: .clinerules-common

## Response Format Guidelines

- Start with a direct answer to the primary question
- Follow with supporting details, examples, or explanations
- Include code snippets when relevant to illustrate the answer
- End with any additional considerations or alternatives
- Use markdown formatting for clarity:
  - Code blocks with language specification
  - Bullet points for lists
  - Headers for sections
  - Bold for emphasis
  - Tables for comparing options

## Technical Deep Dives

When explaining Next.js concepts:

- Reference specific Next.js 14 features like:
  - Server Components vs Client Components
  - Server Actions
  - Parallel Routes
  - Edge Runtime
  - Metadata API
  - App Router

When discussing database topics:

- Address PostgreSQL-specific features
- Explain Prisma model definitions and query methods
- Discuss transaction handling, migrations, and relationships
- Cover indexing strategies specific to the query patterns

When explaining React patterns:

- Focus on functional components and hooks
- Detail the Server Components mental model
- Explain when to use specific hooks (useState, useEffect, useCallback, useMemo)
- Cover Suspense and error boundaries
- Discuss optimizing re-renders

## Architecture Guidance

Provide clear guidelines for:

- Selecting between Server Components and Client Components
- Choosing appropriate data fetching methods:
  - Server Components
  - Server Actions
  - Route Handlers
  - API endpoints
- Structuring the application following the folder structure
- Implementing authentication with NextAuth.js
- Setting up proper error handling
- Implementing logging and monitoring with Sentry

## Practical Problem Solving

When answering how-to questions:

- Provide step-by-step instructions
- Include complete, executable code examples
- Explain the reasoning behind each step
- Address edge cases and potential issues
- Suggest testing strategies for the solution
```

## .clinerules-debug

```markdown
# Debug Mode Rules

version: 1.0.0
import: .clinerules-common

## Systematic Debugging Approach

1. **Identify the Problem**

   - Analyze error messages and stack traces
   - Locate specific line numbers and files
   - Determine if the issue is runtime or build-time
   - Check if the issue is consistent or intermittent

2. **Isolate the Issue**

   - Narrow down to specific component or function
   - Check for recent code changes in that area
   - Create a minimal reproduction case if possible
   - Check if the issue occurs in development, production, or both

3. **Analyze Root Causes**

   - Common Next.js issues:
     - Hydration errors (server/client mismatch)
     - Client component usage errors (hooks in Server Components)
     - Improper data fetching (missing await, no error handling)
     - Missing key props in lists
     - Server/client environment differences
   - Common React issues:
     - State management problems (improper updates)
     - useEffect dependency array issues
     - Missing cleanup in useEffect
     - Incorrect hook usage order
   - Common API issues:
     - CORS configuration problems
     - Missing error handling
     - Improper API response formatting
     - Authentication failures

4. **Implement Solutions**
   - Provide specific code corrections
   - Explain the reasoning behind each fix
   - Address the root cause, not just symptoms
   - Consider performance implications of fixes
   - Add proper error handling to prevent similar issues

## Error Types and Solutions

### Next.js Hydration Errors

- **Symptom**: Text content does not match server-rendered HTML
- **Causes**:
  - Using browser-only APIs (localStorage, window) without checks
  - Dynamic content that differs between server and client renders
  - Missing key props in lists
- **Solutions**:
  - Use useEffect for browser-only code
  - Use dynamic imports with ssr:false for browser-only components
  - Add proper keys to list items
  - Use suppressHydrationWarning only as a last resort

### Data Fetching Issues

- **Symptom**: Missing data, undefined errors, or loading states not showing
- **Causes**:
  - Missing await on async functions
  - Not handling Promise rejections
  - Using client components for data fetching
  - Not implementing proper loading states
- **Solutions**:
  - Use proper async/await with try/catch
  - Move data fetching to Server Components where possible
  - Implement proper loading states with Suspense
  - Use error boundaries for error states

### Performance Problems

- **Symptom**: Slow page loads, jank, or high memory usage
- **Causes**:
  - Too many client components
  - Large bundle sizes
  - Unnecessary re-renders
  - Missing image optimization
  - Inefficient database queries
- **Solutions**:
  - Convert components to Server Components where possible
  - Implement code splitting with dynamic imports
  - Use React.memo for expensive components
  - Optimize database queries with proper indexing
  - Use the Next.js Image component with proper sizing

### Authentication Issues

- **Symptom**: Users can't login or access protected routes
- **Causes**:
  - Incorrect NextAuth.js configuration
  - Missing or incorrect middleware
  - CSRF token issues
  - Cookie configuration problems
- **Solutions**:
  - Check NextAuth.js session handling
  - Verify middleware routes configuration
  - Ensure proper CSRF protection
  - Check cookie settings (httpOnly, secure, sameSite)
```

## .clinerules-data

````markdown
# Data Mode Rules

version: 1.0.0
import: .clinerules-common

## Database Schema Design

- Use UUIDs for primary keys (type: uuid) for better distribution and security
- Include standard audit columns on all tables:
  ```sql
  created_at TIMESTAMP WITH TIME ZONE NOT NULL DEFAULT NOW(),
  updated_at TIMESTAMP WITH TIME ZONE NOT NULL DEFAULT NOW(),
  deleted_at TIMESTAMP WITH TIME ZONE NULL
  ```
````

- Use foreign keys with proper ON DELETE constraints
- Implement check constraints for data validation
- Use appropriate data types:
  - text instead of varchar for variable text
  - integer for small numbers
  - bigint for IDs or large numbers
  - timestamptz for timestamps (not timestamp)
  - jsonb for structured JSON data (not json)
  - enum only for fixed lists that never change
- Apply proper indexing:
  - Indexes on all foreign keys
  - Indexes on frequently queried columns
  - Composite indexes for multi-column queries
  - Partial indexes for filtered queries

## Prisma Schema Best Practices

- Use descriptive model and field names
- Add comprehensive comments for models and fields
- Define proper relations with @relation attribute
- Use enums for fixed value sets
- Implement proper field types matching PostgreSQL types
- Use @@index for indexing frequently queried fields
- Add @@unique constraints for uniqueness requirements
- Implement proper cascading deletes with onDelete: Cascade
- Use middleware for automatic timestamps:
  ```typescript
  // Example middleware for updated_at
  prisma.$use(async (params, next) => {
    if (params.action === "update" || params.action === "updateMany") {
      params.args.data.updated_at = new Date();
    }
    return next(params);
  });
  ```

## Data Access Layer

- Implement a repository pattern for each entity
- Create specific methods for common queries
- Use transactions for multi-step operations
- Handle N+1 query problem with proper includes
- Implement soft deletes instead of hard deletes
- Add pagination for large result sets
- Implement proper error handling and retries
- Create data validation utilities
- Use parameterized queries to prevent SQL injection
- Example structure:

  ```typescript
  // src/infrastructure/database/repositories/user-repository.ts
  export class UserRepository {
    constructor(private prisma: PrismaClient) {}

    async findById(id: string): Promise<User | null> {
      return this.prisma.user.findUnique({
        where: { id, deleted_at: null },
        include: { profile: true },
      });
    }

    async create(data: CreateUserDto): Promise<User> {
      return this.prisma.$transaction(async (tx) => {
        const user = await tx.user.create({
          data: {
            email: data.email,
            // other fields...
            profile: {
              create: data.profile,
            },
          },
        });

        // Additional operations...

        return user;
      });
    }
  }
  ```

## Data Visualization

- Use declarative chart libraries like Recharts
- Implement responsive designs that work across devices
- Format data for better readability (dates, numbers, currencies)
- Include proper loading and error states
- Add tooltips for additional context
- Use appropriate chart types for different data:
  - Line charts for time series
  - Bar charts for comparisons
  - Pie charts for parts of a whole
  - Scatter plots for correlations
  - Tables for detailed data
- Implement proper color schemes for accessibility
- Add legends and axis labels for clarity
- Allow data filtering and interaction

## Data Processing

- Validate input data before processing
- Handle edge cases (empty data, nulls, extreme values)
- Process large datasets in chunks to avoid memory issues
- Use proper error handling with meaningful error messages
- Implement retries for transient failures
- Add logging for debugging and monitoring
- Use appropriate data structures for efficient processing
- Implement caching for expensive operations
- Create unit tests for processing functions

````

# 2. Rules to Add to .github Files

## codeGeneration-instructions.md

```markdown
## Add to General Code Generation
- Implement proper type-checking with TypeScript strict mode
- Use specific version numbers for all dependencies
- Add API versioning strategy with URI-based versions (/v1/resource)
- Implement content security policy with appropriate directives
- Add instrumentation hooks for performance monitoring
- Follow web vitals metrics requirements for UI performance
- Implement accessibility (a11y) best practices with ARIA attributes
- Create decision trees for technology choices
- Add Edge Runtime considerations for global distribution

## Add to Next.js / TypeScript Code Generation
- Use Typescript 5.2+ with strict mode enabled in tsconfig.json
- Target es2022 for modern JavaScript features
- Implement proper error boundaries using error.tsx files
- Configure proper build output with standalone output option
- Add streaming and progressive rendering with React Suspense
- Use Metadata API for SEO optimization
- Implement Core Web Vitals optimization
- Follow accessibility guidelines with proper heading structure and ARIA roles

## Add to Security Section
- Implement proper rate limiting for API endpoints
- Add HTTP security headers (X-Content-Type-Options, X-Frame-Options)
- Use JWT with proper expiration and refresh mechanisms
- Implement proper password hashing with bcrypt or Argon2
- Follow OWASP Top 10 protection guidelines
- Use HTTP-only cookies for sensitive data
- Implement proper CSRF protection with tokens

## Add to Documentation Section
- Generate OpenAPI documentation for all API endpoints
- Create component documentation with Storybook
- Add architectural decision records (ADRs) for major decisions
- Create end-user documentation for features
- Document performance benchmarks and requirements

## Add to Testing Section
- Require 80% minimum code coverage for unit tests
- Implement visual regression testing for UI components
- Add load testing for API endpoints
- Implement contract testing for API boundaries
- Create specific performance testing thresholds
````

## commitMessageGeneration-instructions.md

```markdown
## Add to Commit Message Instructions

- Add scope information in parentheses after type: `feat(auth): add login page`
- Include breaking change notation with BREAKING CHANGE: in the footer
- Reference issue numbers when applicable with #123
- Limit commit message summary line to 72 characters
- Use present tense verbs in commit messages
- Include examples for each commit type:
  - fix: correct input validation in login form
  - feat: add password reset functionality
  - perf: optimize image loading process
  - docs: update API documentation
  - style: format code according to style guide
  - refactor: simplify user authentication logic
  - test: add unit tests for auth service
  - chore: update dependencies to latest versions
- Group related changes in a single commit
- Separate unrelated changes into different commits
```

## copilot-instructions.md

```markdown
## Add to Project Context

- Replace placeholder with specific project description
- Add technology stack with specific versions
- Include business domain description
- Define specific requirements and constraints
- Add performance and scalability expectations
- Include security requirements
- Define user roles and permissions
- Specify target audience and accessibility requirements

## Add to Initial Setup and Architecture

- Add specific Next.js version (14.0.3)
- Define specific database schema requirements
- List specific NextAuth.js providers to implement
- Specify Tailwind and UI component versions

## Add to Testing

- Define specific code coverage requirements (minimum 80%)
- Add performance benchmarks and testing thresholds
- Specify browser compatibility requirements
- Define accessibility testing requirements
```

## reviewSelection-instructions.md

```markdown
## Add to When reviewing the code, consider the following aspects

- Core Web Vitals compliance and performance metrics
- Accessibility (a11y) standards and WCAG compliance
- TypeScript type safety and proper type definitions
- Memory leaks and proper cleanup in useEffect hooks
- Next.js best practices for Server Components and Client Components
- Proper error handling and user feedback
- Internationalization readiness
- Mobile responsiveness and adaptive design

## Add to Format your review

- Include specific performance metrics when discussing performance issues
- Add accessibility scanning results when applicable
- Reference specific style guide rules when noting style issues
- Include security vulnerability severity ratings (High, Medium, Low)
- Add links to relevant documentation for suggested improvements

## Add to Additional guidelines

- Check for compliance with defined architecture patterns
- Verify proper implementation of authentication and authorization
- Assess proper implementation of data validation
- Review error handling comprehensiveness
- Evaluate test coverage for critical paths
```

## testGeneration-instructions.md

```markdown
## Add to Testing Guidelines

- Achieve minimum 80% code coverage for all modules
- Implement performance testing with specific thresholds
- Test accessibility compliance with axe-core
- Add visual regression tests for UI components
- Implement API contract testing
- Add load testing for critical API endpoints
- Test error scenarios and edge cases explicitly
- Implement snapshot testing for UI components

## Add to Playwright E2E Testing Guidelines

- Implement specific performance thresholds for page loads
- Add visual testing for critical UI components
- Test progressive enhancement with JavaScript disabled
- Implement accessibility testing in E2E tests
- Add specific test scenarios for different device sizes
- Create user flow tests that cover critical business processes

## Add to Server Components and Suspense Testing

- Test server-side generation performance metrics
- Add specific tests for incremental static regeneration
- Test streaming performance under network throttling
- Implement accessibility testing for server-rendered content
- Test SEO-specific elements like meta tags and structured data
```

# 3. Rules to Remove

## codeGeneration-instructions.md

1. **Lines 16-17**: Remove "Use functional and declarative programming patterns; avoid classes when possible." as it conflicts with line 215 "Use PascalCase for classes (e.g., UserModel)."

2. **Lines 87-90**: Remove "Implement Server Components and Server Actions for data management" from React Native section as React Native doesn't support Server Components.

3. **Line 133**: Remove "When changing db models, add a migration file and update the schema file (in src/lib/migrations/)" and replace with a more generic path that matches the folder structure defined in the document.

4. **Lines 145-146**: Remove duplicate "Follow semantic versioning for releases" as it's already mentioned in line 144.

5. **Line 175**: Remove "use client" and replace with proper directive `"use client";` with quotes.

6. **Lines 236-239**: Remove Interactive Rules section as it's unclear how to implement these automatic suggestions and may conflict with the LLM's behavior.

## commitMessageGeneration-instructions.md

1. **Line 1**: Fix spelling in heading: "Commit Message Insttructions:" should be "Commit Message Instructions:"

## copilot-instructions.md

1. **Lines 3-7**: Remove placeholder project context and replace with actual project information.

2. **Lines 31-55**: Remove placeholder sections and replace with specific implementation details.

3. **Lines 151-177**: Remove the analysis section at the end as it's not part of the actual instructions.

## reviewSelection-instructions.md

1. **Line 7**: Remove "Remember, you should only suggest significant changes that would meaningfully improve the code, not minor fixes." as it's subjective and may prevent reporting important minor issues.

## testGeneration-instructions.md

1. **Line 85**: Remove reference to "src/lib/migrations/" path and align with the standard folder structure.

2. **Lines 17-18**: Remove "Test across different Chrome versions" and "Test memory usage and performance" from Testing Guidelines and move to a more specific Chrome Extension testing section.
