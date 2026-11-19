# OpenFin — Product Overview

## 1. Introduction

OpenFin is a simulated digital banking platform designed to explore the engineering principles and technical challenges involved in building financial software.

The platform will model common digital banking capabilities, including customer onboarding, account management, internal transfers, payment processing, and transaction history.

It is primarily an engineering project. The focus is on building reliable backend systems and understanding how financial operations should behave under normal conditions, concurrent requests, and failure scenarios.

OpenFin will not handle real customer funds or operate as a licensed financial institution.

## 2. Product vision

Build a modular, independently deployable digital banking platform that demonstrates how financial services can be designed and implemented with correctness, reliability, security, and scalability in mind.

The project should serve as a practical environment for exploring:

- Financial transaction processing.
- Double-entry accounting and ledger design.
- Distributed service communication.
- Event-driven workflows.
- Data consistency and concurrency.
- Payment lifecycle management.
- Reconciliation and operational reliability.

## 3. Product objectives

The main objectives are to:

1. Model customers, accounts, and financial transactions.
2. Implement a reliable double-entry ledger as the financial source of truth.
3. Support simulated transfers between accounts.
4. Explore payment processing through simulated or sandbox integrations.
5. Handle duplicate requests and concurrent financial operations safely.
6. Model asynchronous workflows and recover from partial failures.
7. Reconcile transaction records and identify inconsistencies.
8. Apply security and observability practices across services.

## 4. Intended users

The initial product will model two broad user categories:

### Customers

Customers represent individuals using the simulated banking platform.

They should eventually be able to:

- Register and authenticate.
- Complete a simulated onboarding process.
- View their accounts.
- View account balances and transaction history.
- Initiate internal transfers.
- Initiate supported simulated or sandbox payments.
- View transaction statuses.

### Administrators

Administrators represent internal operators responsible for managing the platform.

Depending on the implementation scope, they should eventually be able to:

- View and manage customer records.
- Inspect accounts and transactions.
- Review transaction failures.
- Investigate reconciliation discrepancies.
- Apply permitted operational actions with appropriate audit records.

Administrative capabilities will be introduced incrementally.

## 5. Core product capabilities

### 5.1 Identity and authentication

Provides customer identity and access management.

Expected capabilities:

- Customer registration.
- Login and authentication.
- Access-token validation.
- Refresh-token management.
- Password management.
- Role-based authorization.
- Session and device management where appropriate.

### 5.2 Customer management

Manages customer profile information and onboarding status.

Expected capabilities:

- Customer profile creation.
- Profile updates.
- Customer status management.
- Simulated onboarding and verification workflows.
- Customer lookup.

### 5.3 Account management

Manages customer accounts and account lifecycle.

Expected capabilities:

- Account creation.
- Account status management.
- Account ownership.
- Account currency.
- Account balance visibility.
- Account transaction history.

Account balance information must be derived from or reconciled against the ledger. It must not become an independent source of financial truth.

### 5.4 Ledger

The ledger is the authoritative record of financial movements within OpenFin.

Expected capabilities:

- Double-entry journal posting.
- Debit and credit entries.
- Journal transaction references.
- Account balance calculations or projections.
- Transaction reversals.
- Ledger history and auditability.

Every posted journal transaction must balance: total debits must equal total credits.

Posted entries must be immutable. Corrections should be represented through compensating or reversal entries.

### 5.5 Transfers

Manages the movement of funds between accounts within OpenFin.

Expected capabilities:

- Beneficiary account validation.
- Transfer initiation.
- Available-balance validation.
- Idempotent request processing.
- Transfer status management.
- Ledger posting.
- Failure handling and recovery.
- Transfer history.

A transfer must not result in funds being debited more than once because of retries or concurrent requests.

### 5.6 Payments

Manages payment workflows involving external payment providers or simulated payment integrations.

Expected capabilities:

- Payment initiation.
- Provider integration.
- Payment status tracking.
- Webhook processing.
- Refund handling.
- Failure and timeout management.
- Provider transaction verification.

The payment workflow must distinguish between confirmed failures and unknown outcomes. A timeout does not automatically mean that a payment failed.

### 5.7 Reconciliation

Compares internal financial records with external or simulated transaction records.

Expected capabilities:

- Transaction record ingestion.
- Transaction matching.
- Identification of unmatched records.
- Detection of amount or status discrepancies.
- Reconciliation reports.
- Resolution tracking.

### 5.8 Risk and transaction controls

Introduces controls to reduce suspicious or invalid transaction activity.

Potential capabilities:

- Transaction limits.
- Velocity checks.
- Suspicious activity indicators.
- Account restrictions.
- Risk scoring.
- Administrative review.

These capabilities will be introduced after the core transaction lifecycle is established.

## 6. Non-functional requirements

OpenFin should progressively satisfy the following requirements.

| Area | Requirement |
|---|---|
| Financial correctness | Financial operations preserve ledger invariants |
| Reliability | Recover from expected dependency and processing failures |
| Idempotency | Prevent duplicate financial effects |
| Consistency | Define consistency expectations between services |
| Security | Protect customer data and restrict access |
| Auditability | Maintain traceable records of financial operations |
| Observability | Provide useful logs, metrics, and distributed traces |
| Maintainability | Keep service responsibilities and interfaces clear |
| Scalability | Allow services to scale independently where necessary |
| Testability | Verify business rules, concurrency, and failure scenarios |

## 7. Out of scope

The initial project will not:

- Hold or process real customer funds.
- Provide licensed banking or financial services.
- Connect to production banking infrastructure.
- Require real identity verification.
- Implement every banking feature from the beginning.
- Introduce infrastructure or technologies without a clear engineering need.

## 8. Product development approach

OpenFin will be developed incrementally.

Each capability should have:

1. A clearly defined business problem.
2. Documented requirements and expected behaviour.
3. An identified service boundary and data owner.
4. An implementation plan.
5. Tests covering normal and failure scenarios.
6. Documentation of important design decisions.

A feature should be considered complete only when its expected behaviour has been implemented and verified, not merely when its API endpoint exists.

## 9. Success criteria

The project will be successful when it demonstrates the ability to:

- Process simulated financial transactions while preserving double-entry ledger invariants.
- Prevent duplicate financial effects during retries.
- Handle concurrent requests without spending the same available funds twice.
- Recover safely from asynchronous processing failures.
- Track and reconcile payment and transfer lifecycles.
- Operate independently deployable services with clear ownership.
- Explain the architecture, trade-offs, and engineering decisions through practical documentation.