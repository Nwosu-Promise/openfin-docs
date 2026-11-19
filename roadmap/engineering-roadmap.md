# OpenFin — Engineering Roadmap

## Purpose

This roadmap defines the implementation sequence for OpenFin.

The project will be developed incrementally, with each milestone introducing a meaningful capability and building on the engineering foundations established in earlier phases.

The priority is to understand and solve the underlying engineering problems, not to maximize the number of services or technologies used.

## Phase 1: Product and engineering foundation

**Objective:** Establish the project's direction, architecture principles, and development conventions.

Deliverables:

- [ ] Define the initial product scope.
- [ ] Document the system architecture.
- [ ] Identify initial service boundaries and responsibilities.
- [ ] Define API conventions and error-response standards.
- [ ] Define event-message conventions.
- [ ] Establish Git and commit conventions.
- [ ] Define documentation and Architecture Decision Record (ADR) practices.
- [ ] Decide the initial local development environment.
- [ ] Create the first service repository when implementation begins.

**Completion criteria:**

The project has a clear product definition, an initial architecture, and enough engineering standards to begin implementation without prematurely designing every future service.

## Phase 2: Identity and customer onboarding

**Objective:** Establish how users are represented and authenticated within OpenFin.

Potential services:

- Identity Service
- Customer Service

Deliverables:

- [ ] Customer registration.
- [ ] Secure password storage.
- [ ] Login and access-token issuance.
- [ ] Refresh-token lifecycle.
- [ ] Authentication middleware or token-validation interface.
- [ ] Customer profile creation.
- [ ] Customer status management.
- [ ] Authorization rules.
- [ ] API documentation.
- [ ] Unit and integration tests.

**Engineering concepts:**

- Authentication and authorization.
- Password hashing.
- Token security.
- Service-to-service authentication.
- Data ownership.
- API versioning.

**Completion criteria:**

A customer can register, authenticate, and retrieve their own profile through authenticated APIs.

## Phase 3: Account management and ledger

**Objective:** Establish the financial foundation of OpenFin.

Potential services:

- Account Service
- Ledger Service

Deliverables:

- [ ] Account creation and lifecycle management.
- [ ] Account ownership and currency definitions.
- [ ] Ledger account model.
- [ ] Journal transaction model.
- [ ] Double-entry debit and credit posting.
- [ ] Atomic journal posting.
- [ ] Immutable posted entries.
- [ ] Reversal and compensating-entry support.
- [ ] Balance calculation or projection.
- [ ] Tests for ledger invariants and concurrent operations.

**Engineering concepts:**

- Double-entry bookkeeping.
- ACID transactions.
- Database constraints.
- Transaction isolation.
- Row-level locking.
- Concurrency control.
- Financial data modelling.

**Completion criteria:**

The system can create accounts and post balanced journal transactions. Every successful posting preserves the invariant that total debits equal total credits.

## Phase 4: Internal transfers

**Objective:** Implement a reliable transfer workflow between OpenFin accounts.

Potential service:

- Transfer Service

Deliverables:

- [ ] Transfer initiation API.
- [ ] Source and destination account validation.
- [ ] Available-balance validation.
- [ ] Transfer state management.
- [ ] Idempotency-key support.
- [ ] Integration with the Ledger Service.
- [ ] Transactional outbox implementation where required.
- [ ] Event publication and consumption.
- [ ] Consumer deduplication.
- [ ] Failure handling and recovery.
- [ ] Concurrent transfer tests.

**Engineering concepts:**

- Distributed transactions.
- Sagas and workflow orchestration.
- Transactional outbox.
- At-least-once message delivery.
- Idempotent consumers.
- Race conditions.
- Retry and timeout strategies.

**Completion criteria:**

A customer can initiate an internal transfer. The system prevents duplicate financial effects, preserves ledger correctness, and handles retries and expected failures safely.

## Phase 5: Payment processing

**Objective:** Extend OpenFin to support payment workflows involving external providers or simulated integrations.

Potential service:

- Payment Service

Deliverables:

- [ ] Payment initiation.
- [ ] Provider integration interface.
- [ ] Simulated or sandbox provider adapter.
- [ ] Payment status lifecycle.
- [ ] Provider reference management.
- [ ] Webhook ingestion.
- [ ] Webhook signature verification where supported.
- [ ] Duplicate webhook handling.
- [ ] Refund workflow.
- [ ] Timeout and unknown-outcome handling.
- [ ] Payment integration tests.

**Engineering concepts:**

- Payment lifecycle modelling.
- External system integration.
- Webhook security.
- Idempotency.
- Retry strategies.
- Compensation and reversal.
- Provider reconciliation.

**Completion criteria:**

The system can initiate and track a simulated or sandbox payment, process provider notifications safely, and distinguish confirmed failures from uncertain outcomes.

## Phase 6: Settlement and reconciliation

**Objective:** Compare internal transaction records with external or simulated provider records.

Potential service:

- Reconciliation Service

Deliverables:

- [ ] Import external transaction records.
- [ ] Define transaction-matching rules.
- [ ] Match internal and external transactions.
- [ ] Identify missing transactions.
- [ ] Identify amount and status discrepancies.
- [ ] Generate reconciliation reports.
- [ ] Track discrepancy resolution.
- [ ] Test duplicate, missing, and mismatched records.

**Engineering concepts:**

- Settlement.
- Financial reconciliation.
- Batch processing.
- Data consistency.
- Idempotent ingestion.
- Audit trails.

**Completion criteria:**

The system can compare internal records with an external dataset and identify transactions that do not reconcile.

## Phase 7: Risk management and transaction controls

**Objective:** Introduce basic controls for transaction activity and account protection.

Potential capabilities:

- [ ] Per-transaction limits.
- [ ] Daily transaction limits.
- [ ] Transaction velocity checks.
- [ ] Suspicious activity indicators.
- [ ] Account restrictions.
- [ ] Risk decision records.
- [ ] Administrative review workflows.

**Engineering concepts:**

- Rule-based risk evaluation.
- Fraud signals.
- Rate limiting.
- Auditability.
- Event-driven risk processing.

**Completion criteria:**

Transactions can be evaluated against defined controls, and the system can explain why an operation was allowed, rejected, or flagged.

## Phase 8: Production readiness and infrastructure

**Objective:** Improve operational reliability and prepare the platform for cloud deployment.

Deliverables:

- [ ] Dockerize individual services.
- [ ] Establish local infrastructure orchestration.
- [ ] Implement centralized structured logging.
- [ ] Add metrics and distributed tracing.
- [ ] Add health and readiness checks.
- [ ] Establish CI pipelines.
- [ ] Add automated integration tests.
- [ ] Introduce infrastructure as code.
- [ ] Deploy selected services to AWS.
- [ ] Configure secrets management.
- [ ] Establish backup and recovery procedures.
- [ ] Perform load and failure testing.
- [ ] Document operational procedures.

**Engineering concepts:**

- Containerization.
- CI/CD.
- Infrastructure as code.
- Cloud networking.
- Observability.
- Capacity planning.
- Disaster recovery.

**Completion criteria:**

The implemented services can be deployed, monitored, tested under load, and recovered from documented failure scenarios.

## How milestones will be executed

Each milestone should follow this workflow:

1. **Understand:** Define the problem and expected behaviour.
2. **Research:** Study the relevant concepts and possible solutions.
3. **Design:** Document the service boundary, data model, interfaces, and trade-offs.
4. **Implement:** Build the smallest meaningful version of the capability.
5. **Verify:** Test business rules, concurrency, and failure scenarios.
6. **Document:** Update the architecture and record important decisions.
7. **Share:** Publish genuine engineering progress and lessons learned.

## Roadmap principles

- Do not create a service repository until there is a concrete reason to implement that service.
- Do not introduce a technology just because it is popular.
- Prefer a working vertical slice over several incomplete components.
- Treat financial correctness as a requirement, not an enhancement.
- Test failure scenarios, not only successful requests.
- Revisit architectural decisions when implementation provides new evidence.
- Keep this roadmap updated as the scope and architecture evolve.

---

**Current status:** Phase 1 — Product and engineering foundation.