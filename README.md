# OpenFin

**A simulated digital banking platform built to explore financial systems, backend engineering, and distributed computing.**

OpenFin is a personal engineering project focused on designing and building the backend infrastructure behind a digital banking platform.

The project is approached from the perspective of a founding backend engineer at an early-stage fintech: making architectural decisions, defining service boundaries, implementing financial workflows, and ensuring that the system is reliable, secure, and maintainable.

The goal is not simply to build a collection of APIs. It is to understand the engineering challenges involved in building financial software and to solve them through practical implementation.

> **Disclaimer:** OpenFin is a simulated project for learning and engineering experimentation. It is not a licensed financial institution, does not provide real banking services, and does not process real customer funds.

## Objectives

Through OpenFin, I intend to explore and implement:

- **Financial systems:** Double-entry bookkeeping, ledgers, account balances, transfers, payments, and transaction reversals.
- **Distributed systems:** Service communication, asynchronous processing, event-driven architecture, consistency, and fault tolerance.
- **Financial correctness:** Idempotency, concurrency control, immutable transaction records, and reconciliation.
- **Security:** Authentication, authorization, secure service communication, and protection of sensitive data.
- **Reliability:** Retries, timeouts, failure recovery, observability, and operational resilience.
- **Infrastructure:** Containerization, CI/CD, cloud deployment, monitoring, and infrastructure as code.

## Architecture

OpenFin will use a microservices architecture.

Each service will:

- Live in its own Git repository.
- Own its application logic and data.
- Have its own dependencies, tests, configuration, and deployment lifecycle.
- Communicate with other services through explicitly defined APIs and asynchronous events.
- Be independently developed and deployable.

The architecture will evolve as the project grows. Services will be introduced when their responsibilities and boundaries become clear, rather than creating every possible service upfront.

The project will also explore polyglot development, choosing technologies based on the requirements of individual services.

## Engineering principles

The following principles will guide implementation:

1. **Financial correctness first:** A successful API response is not enough; financial operations must preserve their invariants.
2. **Explicit data ownership:** A service owns its data. Other services interact with it through documented interfaces.
3. **Immutable financial history:** Posted financial records should not be silently modified or deleted. Corrections should be represented through reversals or compensating entries.
4. **Idempotent operations:** Retrying a request must not accidentally execute a financial operation more than once.
5. **Failure is expected:** Timeouts, duplicate messages, unavailable dependencies, and partial failures must be considered in system design.
6. **Observable systems:** Logs, metrics, traces, and operational signals should help explain what the system is doing.
7. **Document important decisions:** Significant architectural choices and their trade-offs should be recorded.

## Repository structure

This repository is the central engineering documentation repository for OpenFin.

It contains:

- Product requirements and scope.
- System architecture and service boundaries.
- Engineering standards and conventions.
- Architecture Decision Records (ADRs).
- Implementation roadmap and technical documentation.

Individual services will be created in separate repositories as implementation progresses.

## Project roadmap

The project will be implemented incrementally:

1. Product definition and engineering foundation.
2. Identity and customer onboarding.
3. Accounts and ledger.
4. Internal transfers.
5. Payment processing.
6. Settlement and reconciliation.
7. Risk management and transaction limits.
8. Production readiness and cloud infrastructure.

See [Engineering Roadmap](roadmap/engineering-roadmap.md) for details.

## Building in public

OpenFin is also an opportunity to learn, experiment, document engineering decisions, and share practical lessons.

Progress and technical discussions will be shared through:

- **GitHub:** Source code, tests, documentation, and architecture decisions.
- **LinkedIn:** Engineering progress, lessons, and project milestones.
- **X:** Short updates, discoveries, and technical discussions.
- **Blog:** Detailed technical articles and implementation breakdowns.

The intention is to share what is actually being designed, implemented, tested, and learned throughout the project.

## Project status

**Current phase:** Foundation and architecture definition.

This repository is the starting point. Implementation will progress through small, verifiable milestones, with architecture and documentation updated as the system evolves.