# Analysis Guide

Detailed procedures for analyzing brownfield projects.

## Table of Contents

- [Tech Stack Identification](#tech-stack)
- [Architecture Recognition](#architecture)
- [Conventions Extraction](#conventions)
- [Module Analysis](#modules)
- [Pattern Recognition](#patterns)

---

## Tech Stack

### Primary Programming Languages

1. Identify file extension distribution (.java, .ts, .py, .go, .rs, .cs, .fs, .vb, etc.)
2. Determine language version constraints (package.json engines, pom.xml properties, global.json sdk version)
3. Identify if multi-language project

### Frameworks and Runtimes

| Category | Examples |
|----------|----------|
| Web frameworks | Spring Boot, Express, Django, Gin, Actix, ASP.NET Core, Blazor |
| Frontend frameworks | React, Vue, Angular, Svelte, Blazor WebAssembly |
| Runtimes | Node.js, JVM, Python, Go, .NET Runtime, .NET Framework |

### Build Tools and Package Managers

- Build: Maven, Gradle, npm/yarn/pnpm, cargo, go build, MSBuild, dotnet CLI
- Dependencies: Config files and lock files (packages.lock.json, packages.config, Directory.Packages.props)

### Testing Frameworks

| Type | Examples |
|------|----------|
| Unit | JUnit, Jest, pytest, go test, xUnit, NUnit, MSTest |
| Integration | Testcontainers, Supertest, ASP.NET Core TestServer |
| E2E | Playwright, Cypress, Selenium, SpecFlow |

### Data Storage

- Databases: MySQL, PostgreSQL, MongoDB, Redis, SQL Server, CosmosDB
- ORM/ODM: JPA, Prisma, SQLAlchemy, GORM, Entity Framework Core, Dapper

### Infrastructure

- Containerization: Docker, docker-compose
- CI/CD: GitHub Actions, GitLab CI, Jenkins
- Cloud: AWS, GCP, Azure

---

## Architecture

### Pattern Recognition

| Pattern | Recognition Features | Key Directories |
|---------|---------------------|-----------------|
| Layered | controller/service/repository | src/main/java/.../controller, Controllers/, Services/ |
| Onion | domain/application/infrastructure | src/domain, src/infrastructure, Domain/, Infrastructure/ |
| Hexagonal | ports/adapters | src/adapters, src/ports, Adapters/, Ports/ |
| Microservices | Independent service directories | services/, apps/, Services/ |
| Monorepo | Multiple packages coexist | packages/, apps/, libs/, src/Services/ |
| Modular Monolith | Feature-based modules | modules/, features/, Modules/ |
| Clean Architecture | Core/Application/Infrastructure/Web | Core/, Application/, Infrastructure/, WebApi/ |
| DDD | Bounded contexts and aggregates | Domain/, Application/, Infrastructure/ |

### Code Organization

- **Layer-first**: controllers/, services/, models/
- **Feature-first**: users/, orders/, payments/
- **Hybrid**: Identify primary and secondary organization

---

## Conventions

### Naming Conventions

| Type | Options |
|------|---------|
| File naming | kebab-case, PascalCase, snake_case |
| Variables | camelCase, snake_case, _camelCase (private fields in C#) |
| Classes | PascalCase, I-prefix for interfaces (C#/TypeScript) |
| Constants | UPPER_SNAKE_CASE, PascalCase (C#) |
| Namespaces | PascalCase with dots (C#: Company.Product.Feature) |

### Code Style

Extract from config files:
- Indentation (spaces/tabs, count)
- Quotes (single/double)
- Semicolons (yes/no)
- Line length limit
- Import organization

### Comment Standards

- Doc format: JSDoc, Javadoc, docstring, XML documentation comments (C#)
- Inline style
- TODO/FIXME conventions
- Region directives (#region/#endregion in C#)

### Git Conventions

- Commit format: Conventional Commits or custom
- Branch naming strategy
- PR/MR templates

---

## Modules

### For Multi-Module Projects

1. **Enumerate all modules**:

| Module | Path | Type | Responsibility |
|--------|------|------|----------------|
| [name] | [path] | api/service/dao/common | [description] |

2. **Analyze responsibilities**:
   - API/Interface layer (Contracts, DTOs)
   - Service implementation layer (Business logic, Application services)
   - Data access layer (Repositories, DbContext, Entities)
   - Common utilities layer (Shared components, Cross-cutting concerns)
   - Web/API layer (Controllers, Minimal APIs, Middleware)
   - Test projects (Unit tests, Integration tests)

3. **Map dependencies**:
   - Dependency graph
   - Allowed/forbidden directions
   - Cross-module communication

---

## Patterns

### Design Patterns to Identify

- Repository Pattern
- Service Layer Pattern
- Factory Pattern
- Strategy Pattern

### Code Organization Patterns

- DTO/VO/Entity separation
- Interface/implementation separation
- Configuration externalization
- Dependency injection

### Error Handling

- Exception hierarchy
- Unified error response format
- Error code standards

### Logging and Observability

- Logging framework and format
- Distributed tracing
- Metrics collection
