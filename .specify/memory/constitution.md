# ContosoDashboard Constitution

## Core Principles

### I. Blazor-First UI Architecture
All user interface components must be built using Blazor. UI logic should be component-based, reusable, and maintainable within the Blazor framework ecosystem.

### II. Entity Framework Core for Data Access
All database operations must go through Entity Framework Core (EF Core). Direct SQL queries are prohibited. ORM patterns must be consistently applied across all services.

### III. Test-First Development (NON-NEGOTIABLE)
TDD is mandatory: Tests written → Code reviewed → Tests fail → Implementation begins. Both unit tests (xUnit) and integration tests are required for all features. Minimum 70% code coverage is non-negotiable.

### IV. Server-Side Validation & Security
All input validation must occur server-side. Client-side validation is supplementary only. Personally Identifiable Information (PII) must be encrypted at rest. Authentication uses ASP.NET Core Identity with Role-Based Access Control (RBAC).

### V. Quality Gate Enforcement
Code must pass automated linting, SonarQube quality gates, and require peer review before integration. No compilation warnings or critical code smells allowed in main/develop branches.

## Technology Stack

- **UI Framework**: Blazor (Server or WebAssembly)
- **Data Access**: Entity Framework Core
- **Authentication**: ASP.NET Core Identity with RBAC
- **Testing Framework**: xUnit
- **Quality Tools**: SonarQube, linting (StyleCop/Roslyn analyzers)
- **Security**: Server-side validation, PII encryption at rest

## Testing Requirements

- **Unit Tests**: Required for all business logic; xUnit framework mandatory
- **Integration Tests**: Required for data access, service interactions, and API contracts
- **Code Coverage**: Minimum 70% across the codebase
- **Test Automation**: All tests must run in CI/CD pipeline and block merge if failures occur
- **Test Data**: Use realistic, sanitized test data; never use production PII in test environments

## Security & Data Handling

- **Authentication/Authorization**: ASP.NET Core Identity with role-based authorization (RBAC)
- **Data Validation**: Server-side validation required for all inputs; no reliance on client-side validation
- **Sensitive Data (PII)**: Must be encrypted at rest; apply principle of least privilege
- **Secrets Management**: Use configuration secrets, never hardcode credentials
- **Audit Logging**: Log security-relevant events (login attempts, data access, privilege changes)

## Development Workflow

### Git Strategy: Git Flow
- **main**: Production-ready releases only
- **develop**: Integration branch for features and bugfixes
- **feature/***: Individual feature branches off develop
- **release/***: Release preparation branches
- **hotfix/***: Emergency fixes off main

### Branching Rules
- All work starts from a feature branch
- Commit messages follow conventional format: `[TYPE]: [Message]` (e.g., `feat: add user authentication`, `fix: resolve PII encryption bug`)
- Feature branches must be kept short-lived (max 2 weeks active development)

### Code Review & PR Standards
- **Minimum Approvals**: 2 approved reviews required before merge
- **Automated Checks**: All tests must pass; SonarQube quality gate must be met; no build failures
- **Review Focus**: Correctness, security, test coverage, code style, documentation
- **Merge Strategy**: Squash commits for clean history; never force-push to main/develop

## Definition of Done

A feature is considered "Done" when ALL of the following criteria are met:

1. ✅ Code is written, commented, and follows project style guide
2. ✅ Minimum 2 peer reviews completed and approved
3. ✅ Unit tests written with ≥70% coverage for new/modified code
4. ✅ Integration tests written and all tests passing
5. ✅ Code passes linting and SonarQube quality gates
6. ✅ Documentation updated (inline comments, README sections, API documentation if applicable)
7. ✅ Feature branch merged to develop (then to main via release process)

## Governance

**Constitution Authority**: This constitution supersedes all other coding practices and guidelines for ContosoDashboard.

**Enforcement**: 
- All PRs must be verified for compliance with this constitution
- Code review checklist must reference applicable sections
- Quality gates in CI/CD pipeline enforce technical requirements

**Amendments**: 
- Proposed changes require team consensus
- Amendments must be documented with rationale and date
- All team members must be notified of changes

---

**Version**: 1.0.0 | **Ratified**: 2026-03-19 | **Last Amended**: 2026-03-19
