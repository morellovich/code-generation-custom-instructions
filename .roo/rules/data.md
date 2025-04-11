# Data Mode Rules

version: 1.0.0

# This file contains rules specific to data handling, database interactions, processing, and visualization.

# It assumes the principles and conventions from common.md and architect.md are followed.

## Database Schema & Interaction (PostgreSQL & Prisma)

- Use UUIDs for primary keys (`@id @default(uuid())` in Prisma).
- Include standard audit columns (`createdAt`, `updatedAt`, `deletedAt`) on all relevant tables. Use `@default(now())` and `@updatedAt`.
- Implement soft deletes using a `deletedAt DateTime?` field and filter queries (`where: { deletedAt: null }`).
- Use appropriate data types: `DateTime` (for `TIMESTAMPTZ`), `String` (for `TEXT`), `Json` (for `JSONB`), `Int`, `BigInt`, `Float`, `Boolean`.
- Define relations explicitly using `@relation` with appropriate `fields` and `references`. Specify `onDelete` behavior (e.g., `Cascade`, `SetNull`, `Restrict`).
- Apply database-level constraints (`@unique`, `@@unique`, potentially `CHECK` via raw SQL migrations if needed).
- Use Prisma Migrate (`prisma migrate dev`) for all schema changes; write descriptive migration names.
- Optimize queries by using `select` or `include` to fetch only necessary data and prevent N+1 problems.
- Use `prisma.$transaction([...])` for operations requiring atomicity.
- Implement connection pooling appropriately based on expected load (configure in connection string or Prisma Client options).
- Analyze query performance using `EXPLAIN ANALYZE` and add/adjust indexes (`@index`, `@@index`) accordingly (on foreign keys, frequently filtered/sorted columns).

## Data Access Layer (Repository Pattern)

- Create repository classes/modules for each core domain entity (e.g., `UserRepository`, `ProductRepository`).
- Inject PrismaClient into repositories (e.g., via constructor or dependency injection).
- Encapsulate common queries within repository methods (e.g., `findById`, `findByEmail`, `listActiveUsers`).
- Handle pagination logic within repository methods (using `skip`, `take`).
- Implement filtering and sorting logic based on parameters passed to repository methods.
- Ensure repository methods consistently handle soft deletes (filtering by `deletedAt: null`).
- Abstract away complex Prisma query logic within the repository.

  ```typescript
  // Example: src/infrastructure/database/repositories/user.repository.ts
  import { PrismaClient, User } from "@prisma/client";

  export class UserRepository {
    constructor(private prisma: PrismaClient) {}

    async findById(id: string): Promise<User | null> {
      return this.prisma.user.findUnique({
        where: { id, deletedAt: null },
        include: { profile: true }, // Example include
      });
    }

    async listActive(page: number, pageSize: number): Promise<User[]> {
      return this.prisma.user.findMany({
        where: { deletedAt: null },
        skip: (page - 1) * pageSize,
        take: pageSize,
        orderBy: { createdAt: "desc" },
      });
    }
    // Define other methods like create, update, softDelete here
  }
  ```

## Data Processing & Validation

- Validate incoming data using Pydantic models (in FastAPI) or validation libraries (e.g., Zod) before processing or database insertion.
- Implement data cleaning steps for user-provided or external data (trimming strings, handling nulls, standardizing formats).
- Process large datasets in batches or streams to avoid memory exhaustion.
- Use appropriate data structures (Maps, Sets) for efficient lookups during processing.
- Handle potential errors during processing gracefully (e.g., using `try/catch`, logging errors, returning meaningful error responses).
- For complex data transformations in Python, consider using libraries like Pandas if appropriate for the task complexity.

## Data Visualization (Frontend)

- Choose appropriate chart types based on the data and the insight to convey (e.g., line for trends, bar for comparisons, pie for proportions, scatter for correlation).
- Use a declarative charting library (e.g., Recharts, Nivo) compatible with React/Next.js.
- Ensure charts are responsive and adapt to different screen sizes.
- Implement accessibility features: proper color contrast, ARIA labels, keyboard navigation if interactive.
- Provide clear titles, axis labels, and legends.
- Include tooltips for displaying detailed data on hover.
- Implement loading states (e.g., skeleton loaders) while data is fetching.
- Handle error states gracefully if data fails to load.
- Consider performance for large datasets (e.g., data aggregation before rendering, virtualization).

## Data Security

- Never expose raw database errors to the client; log them securely on the server.
- Implement Role-Based Access Control (RBAC) at the data access layer or API level to restrict access based on user roles.
- Consider Row-Level Security (RLS) in PostgreSQL for fine-grained data access control if needed.
- Sanitize all inputs used in database queries (Prisma Client handles this for standard queries, be careful with `$queryRaw`).
- Mask or omit sensitive data in API responses and logs.
- Encrypt sensitive data at rest if required by compliance standards.
