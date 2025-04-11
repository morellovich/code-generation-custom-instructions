# Architect Mode Rules

version: 1.0.0

# This file contains rules for high-level system design and architecture.

# It assumes the principles and conventions from common.md are followed.

## Architecture Goals & Principles

- Design scalable, maintainable, and efficient architectures.
- Adhere to Clean Architecture principles, ensuring clear separation of concerns (Domain, Application, Infrastructure, Presentation).
- Apply SOLID principles:
  - **Single Responsibility (SRP):** E.g., A `UserService` handles user creation/updates, while a separate `AuthService` handles login/logout. Don't combine unrelated responsibilities.
  - **Open/Closed (OCP):** E.g., Use dependency injection (FastAPI `Depends`) or strategy patterns so new functionality (like adding a new notification type) can be added without modifying existing core services.
  - **Liskov Substitution (LSP):** E.g., If `AdminUser` inherits from `BaseUser`, an `AdminUser` instance should be usable anywhere a `BaseUser` is expected without breaking functionality.
  - **Interface Segregation (ISP):** E.g., Define separate `IUserReader` and `IUserWriter` interfaces instead of one large `IUserRepository` if some clients only need read access.
  - **Dependency Inversion (DIP):** E.g., High-level modules (use cases) should depend on abstractions (interfaces like `IUserRepository`), not concrete low-level implementations (`PrismaUserRepository`). Use dependency injection to provide the concrete implementation.
- Maintain a single source of truth for common rules and configurations (referencing `common.md`).
- Use decision trees or ADRs (Architecture Decision Records) for significant technical choices.
- Ensure the chosen architecture supports the specified technology stack (`common.md`).

## System Design Patterns

- Utilize Domain-Driven Design (DDD) for complex business logic:
  - Define clear Bounded Contexts (e.g., "Authentication", "Ordering", "Inventory").
  - Use Ubiquitous Language shared between developers and domain experts.
  - Implement Aggregates (e.g., `Order` with `OrderLine` items) to enforce invariants.
  - Define Entities (objects with identity, e.g., `User`) and Value Objects (objects defined by attributes, e.g., `Address`, `EmailAddress`).
  - Place domain logic within domain entities or domain services, not application services.
- Implement Repository pattern for data access abstraction.
- Use Dependency Injection (e.g., FastAPI `Depends`) for managing dependencies.
- Employ message queues (e.g., RabbitMQ, Kafka - if applicable) for decoupling services and handling asynchronous tasks.
- Implement caching strategies at appropriate levels (CDN, application, database).

## API Design (FastAPI)

- Follow RESTful principles with clear resource naming and standard HTTP methods.
- Implement API versioning using URI path (e.g., `/api/v1/...`).
- Use Pydantic models for request/response validation and serialization.
- Return standard HTTP status codes consistently.
- Generate and maintain accurate OpenAPI documentation (`/docs`, `/redoc`).
- Implement rate limiting on public or sensitive endpoints.
- Ensure proper CORS configuration.
- Design for statelessness where possible; manage state explicitly when necessary.

## Database Design (PostgreSQL & Prisma)

- Normalize database schema (typically to 3NF) unless performance justifies denormalization.
- Use UUIDs for primary keys where appropriate.
- Enforce data integrity with `NOT NULL`, `UNIQUE`, `CHECK` constraints, and foreign keys.
- Define clear relationships in `schema.prisma` using `@relation`.
- Implement soft deletes (`deletedAt` timestamp) for critical data.
- Use Prisma Migrate for all schema changes (`prisma migrate dev`).
- Apply indexing strategies (on foreign keys, frequently queried columns, composite indexes) based on query patterns. Analyze query performance (`EXPLAIN ANALYZE`).
- Use appropriate data types (e.g., `TIMESTAMPTZ`, `TEXT`, `JSONB`).
- Configure connection pooling appropriately for the expected load.

## Authentication & Security Architecture (NextAuth.js)

- Implement robust authentication flows (OAuth, JWT, potentially MFA).
- Use NextAuth.js adapters for database session storage (e.g., Prisma adapter).
- Enforce Role-Based Access Control (RBAC) using middleware or similar mechanisms.
- Secure sensitive routes and API endpoints.
- Implement CSRF protection (e.g., NextAuth.js built-in protection).
- Use secure cookie settings (`HttpOnly`, `Secure`, `SameSite=Lax` or `Strict`).
- Implement Content Security Policy (CSP) to mitigate XSS attacks.
- Ensure all user inputs are sanitized and validated.
- Store passwords securely using strong hashing algorithms (bcrypt/Argon2).
- Use HTTPS for all communication.

## Performance & Scalability

- Design for horizontal scalability (stateless services where possible).
- Implement caching strategies (CDN, application-level, database query caching).
- Optimize database queries and indexing.
- Use asynchronous operations (`async def` in FastAPI, background tasks) for I/O-bound tasks.
- Consider using read replicas for read-heavy database workloads.
- Optimize frontend performance (refer to `code.md` rules like Server Components, image optimization, code splitting).
- Monitor performance using tools like Sentry and analyze Core Web Vitals.
- Consider Edge Runtime (e.g., Vercel Edge Functions) for latency-sensitive API routes or middleware.

## Deployment Architecture (Docker / Coolify)

- Use multi-stage Docker builds for smaller, optimized images.
- Implement health checks in Docker containers.
- Manage configuration and secrets securely using environment variables or a secrets manager.
- Set up CI/CD pipelines (e.g., GitHub Actions) for automated testing and deployment.
- Plan for automated database backups and recovery.
- Implement structured logging across all services.
