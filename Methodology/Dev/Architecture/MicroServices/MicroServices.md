# Micro Services

## Pros, Cons

## Monolith, MicroServices, NanoServices, Hybrid, Lambda Functions

## MicroServices

### Design

How many Micro-Services? What responsibility get each Micro-Service?

- By Data Model
- By Isolated Logics
- Modularity and Single Responsibility principles
- Size?

Common Challenges

- Low latency
  - Services should be physically close
- Maintenance
  - Orchestrator
    - ApiGateway, LB, Service Discovery, Containers
  - Services Cross-Cutting Concern
    - Solve it once for all Micro-Services
- Dealing with [Transaction](Transactions.md) in between services
- The Join Queries challenge
  - Create another service with a shared DataBase table/view.
  - Might be a sign of bad division to services
