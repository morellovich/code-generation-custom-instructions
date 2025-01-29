## Preferred Technology Stack and Versions

Generate code using ONLY the following technologies and their specified versions:

    - **Frontend:**
    - Next.js:Version 13.4.12
    - Tailwind CSS:Version 3.3.2
    - React Native:Version 0.72.3

    - **Backend:**
    - FastAPI:Version 0.100.0

    - **Database:**
    - PostgreSQL:Version 15.3

    - **ORM:**
    - Prisma:Version 4.15.0
    - **Authentication:**
    - NextAuth.js (Auth.js):Version 4.22.1

    - **Testing:**
    - Jest:Version 29.6.1
    - React Testing Library:Version 14.0.0
    - Pytest:Version 7.4.0

    - **Logging and Monitoring:**
    - Sentry SDK for JavaScript:Version 7.59.0
    - Sentry SDK for Python:Version 1.29.2

    - **Containerization and Deployment:**
    - Docker:Version 24.0.5
    - Coolify:Version 3.8.0

## Instructions for Next.js code generating:

    - Utilize functional components and hooks for better state management, enhancing user interaction experiences
    - Use functional components, state management, and React hooks to achieve smooth page transitions 2

## Instructions for Tailwind CSS code generating:

    - Keep utility classes organized with meaningful names to facilitate easier maintenance and integration with other frameworks 1
    - Optimize by avoiding excessive nesting, which can bloat the final CSS output and degrade performance 3

## Instructions for React Native code generating:

    - Prioritize component reusability and use TypeScript for type safety, improving both functionality and ease of development 5
    - Minimize state usage to avoid becoming a performance bottleneck, only maintaining necessary state for optimal efficiency 3
    - Organize project structure clearly to enhance maintainability and facilitate robust testing practices 1

## Instructions for FastAPI code generating:

    - Write asynchronous functions wherever possible to improve scalability and resource utilization
    - Provide clear examples of endpoint definitions with proper error handling to ensure secure and reliable API interactions

## Instructions for PostgreSQL code generating:

    - Emphasize normalization principles while designing schemas and include indexing strategies in comments for query optimization 5
    - Design databases with failover mechanisms and backup procedures to ensure high availability and reliability
    - Define roles and permissions explicitly to control access and protect sensitive data

## Instructions for Prisma code generating:

    - Specify conventions for naming models and fields, enabling Prisma Client's features like transactions for complex operations 5
    - Encourage the use of mock data and transactional tests to ensure efficient and effective database interactions

## Instructions for NextAuth.js (Auth.js) code generating:

    - Detail the expected flow of authentication processes, including session management and token storage mechanisms 5
    - Highlight security considerations such as CSRF protection and secure cookie settings to ensure reliable and available services

## Instructions for Jest & React Testing Library / Pytest code generating:

    - Focus on writing comprehensive tests that cover edge cases and unexpected inputs, ensuring system reliability
    - Leverage fixtures for setup and teardown processes in Pytest to streamline testing workflows 5
    - Encourage descriptive test names and setup steps in comments to assist Copilot in generating understandable test suites

## Instructions for Sentry code generating:

    - Outline how errors should be captured and reported, including environment-specific configurations to safeguard sensitive information 5
    - Comment about customizing breadcrumbs and user context to provide rich error details, aiding in quicker resolution and higher service availability

## Instructions for Docker code generating:

    Define base images and layering strategies to optimize build times and resource usage
    - Add comments about multi-stage builds and environment variable usage to steer Copilot towards creating efficient and user-friendly Dockerfiles 5
    - Implement health checks and restart policies to ensure containers are always running and ready to serve requests

## Coding Conventions and Best Practices:

    - **Code Consistency:Ensure that all code adheres to the specified versions of the technologies listed above to maintain consistency across projects.
    - **Error Handling:Implement robust error handling mechanisms. For example, in FastAPI, use exception handlers to manage errors gracefully.
    - **Testing:Write comprehensive tests for all functionalities. Utilize the specified testing frameworks to ensure code reliability.
    - **Logging:Integrate logging using the specified Sentry SDKs to monitor and debug applications effectively.
    - **Documentation:Provide clear and concise documentation for all modules and functions. Use docstrings in Python and JSDoc in JavaScript/TypeScript where applicable.
    - **Code Formatting:Adhere to standard code formatting guidelines. For instance, use Prettier for JavaScript/TypeScript and Black for Python to maintain uniformity.
    - **Version Control:Follow semantic versioning for all projects and ensure that version numbers are updated appropriately with each release.
