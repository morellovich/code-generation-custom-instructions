# This is a project-specific instructions, and it's a placeholder.

## Project Context

[Brief description ]

- [more description]
- [more description]
- [more description]

Here's a structured sequence of prompts to develop a web app following your instructions:

### Initial Setup and Architecture

1. Create a Next.js 14 project structure following the specified folder structure, including all necessary configuration files (.gitignore, tsconfig.json, etc.)

2. Set up the database schema with Prisma for a [your app's main feature] system, including user authentication tables

3. Create the authentication system using NextAuth.js with the following providers: [list providers], including protected routes and middleware

4. Set up Tailwind CSS and Shadcn UI basic configuration, including a theme configuration file

### Core Features Development

5. Create the main layout component with responsive navigation and footer, using Server Components where possible

6. Implement the home page with [main feature] showcase, using Server Components for data fetching

7. Create user dashboard page with Server Components for data display and Client Components for interactivity

8. Implement data fetching layer with Server Actions for [main feature] CRUD operations

### Authentication and Security

9. Set up role-based access control (RBAC) system using middleware and protected routes

10. Implement form validation and input sanitization utilities using [preferred validation library]

### Database and API

11. Create database migrations for [feature] tables and implement the Data Access Layer

12. Set up API route handlers for necessary endpoints that can't use Server Actions

### UI Components

13. Create reusable form components with proper validation and error handling

14. Implement data table component with sorting, filtering, and pagination

### State Management and Data Flow

15. Set up global state management using Server Components and minimal Client state

16. Implement optimistic updates for better user experience in forms and data mutations

### Testing

17. Create unit tests for utilities and components using Jest and React Testing Library

18. Set up E2E tests using Playwright for critical user flows

### Performance and Monitoring

19. Implement Sentry error tracking and performance monitoring

20. Set up logging system with structured logging for debugging

### Deployment and CI/CD

21. Create Docker configuration for development and production environments

22. Set up CI/CD pipeline with GitHub Actions for testing and deployment

### Final Steps

23. Implement SEO optimization with metadata and Open Graph tags

24. Create comprehensive documentation including API documentation and setup instructions

For each prompt, provide:

- The specific requirements you need
- Any special considerations
- Expected functionality
- Design preferences

This will help me generate more accurate and useful code following your instructions. Would you like to start with the first prompt?

Collecting workspace informationLet me analyze the instruction files systematically.

### 1. Problematic Areas

- **Length Issues**:

  - The codeGeneration-instructions.md is quite lengthy and could benefit from better organization
  - The project context section in copilot-instructions.md is empty/placeholder

- **Unclear Instructions**:
  - The interactive rules section doesn't specify how to implement the automatic suggestions
  - Some version numbers are outdated (Next.js 13.4.12 when 14.x is current)

### 2. Conflicts

1. **Architecture Conflicts**:

```markdown
- "Use functional and declarative programming patterns; avoid classes"
  vs
- "Use PascalCase for classes (e.g., UserModel)"
```

2. **State Management Conflicts**:

```markdown
- "Minimize state usage to avoid performance bottlenecks"
  vs
- "Use React Context for global state when needed"
```

### 3. Repetitive Rules

1. **Error Handling** appears in multiple sections:

```markdown
- General Code Generation section
- FastAPI section
- Error Handling section
- Chrome Extension rules
```

2. **Testing** instructions are spread across:

```markdown
- General Code Generation section
- Testing Frameworks section
- Testing section
- testGeneration-instructions.md
```

### 4. Non-Best Practice Phrases

1. **Outdated Patterns**:

```markdown
- References to classes when functional approach is preferred
- Some Tailwind practices could be updated for v3.3+ best practices
```

### 5. Testing/Debugging Assessment

The testing section is well-structured, especially in testGeneration-instructions.md. However, suggestions for improvement:

- Add specific code coverage requirements
- Include performance testing metrics
- Add more specific E2E testing scenarios

### 6. Instructions Volume Assessment

The volume is manageable but could be better organized. Suggestion:

- Create a centralized index
- Split into domain-specific modules
- Use cross-references instead of repetition

### 7. Comprehension

Yes, the instructions are generally clear and technically sound.

### 8. Suggestions

1. **Structure Improvements**:

```markdown
- Create an index file linking to specific instruction sets
- Use a hierarchical structure for related rules
- Implement versioning for instruction sets
```

2. **Technical Updates**:

```markdown
- Add TypeScript strict mode requirements
- Include Web Vitals metrics requirements
- Add accessibility (a11y) requirements
- Include API versioning strategy
```

3. **Process Improvements**:

```markdown
- Add PR template requirements
- Include documentation generation rules
- Add changelog maintenance guidelines
```

4. **Modern Practices**:

```markdown
- Add Edge Runtime considerations
- Include Server Actions guidelines
- Add streaming and progressive rendering rules
```

5. **Organization**:

```markdown
- Create separate files for framework-specific rules
- Maintain a single source of truth for common rules
- Include decision trees for technical choices
```

These changes would make the instructions more maintainable and easier to follow while reducing redundancy and conflicts.
