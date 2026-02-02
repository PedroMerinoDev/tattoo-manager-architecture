# Tattoo Manager SaaS Architecture 🏛️

> **Engineering Overview of a Production ERP System**

This repository serves as a **Documentation & Architecture Showcase** for **Tattoo Manager**, a mature SaaS platform serving thousands of studios. 

**Note:** The source code is proprietary. This repository demonstrates the engineering principles, architectural decisions, and code quality standards applied in the project.

## System Overview

Tattoo Manager is a Multi-Tenant ERP handling:
- Scheduling & Calendar Management
- Financial Transactions (Split Payments)
- Anamnesis & Legal Forms
- Inventory Control
- Push Notifications & CRM

## Architecture: The Core

We strictly follow **Clean Architecture** principles to ensure decoupling and testability.

### Layers

1.  **Domain Layer (Pure Dart/Java):**
    *   Entities (Enterprise Business Rules)
    *   Use Cases (Application Business Rules)
    *   *Zero dependencies on frameworks (Flutter/Spring).*

2.  **Infrastructure Layer:**
    *   Repositories Implementations
    *   External APIs (Stripe, Firebase, Brevo)
    *   Database adaptors (PostgreSQL / Hive)

3.  **Presentation Layer:**
    *   Controllers / BLoCs
    *   UI Components (Design System)

## Design Patterns Used

- **Repository Pattern:** To abstract data sources.
- **Adapter Pattern:** To isolate external services (Payment Gateways).
- **Factory Pattern:** For complex object creation (User Roles policies).
- **Decorator Pattern:** For extending core functionalities without inheritance hell.

## Testing Strategy (The Pyramid)

We enforce a strict testing culture:
- **Unit Tests:** 100% coverage on Domain Entities and Use Cases. (Mock-free logic).
- **Integration Tests:** Verifying Infrastructure <-> Database contracts.
- **Widget/UI Tests:** Ensuring critical flows (Checkout, Login) never break.

## CI/CD Pipeline

- **Commit:** Triggers linting & unit tests.
- **Merge Request:** Triggers integration tests & build check.
- **Release:** Automated deploy to Stores (App Center / Play Store).

---
*Architected by [Pedro Merino](https://github.com/pedromerino)*
