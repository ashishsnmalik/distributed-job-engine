# Development Methodology

## Distributed Job Execution Platform --- Go

**Document type:** Project development framework\
**Status:** Proposed baseline\
**Applies to:** All project versions, from `v0.1.0` onward

------------------------------------------------------------------------

## 1. Purpose

We will develop the Distributed Job Execution Platform using a
professional, AI-assisted, version-driven software development
lifecycle.

The project has three equally important objectives:

1.  **Product development:** Build a reliable, extensible distributed
    job execution platform.
2.  **Engineering practices:** Learn and apply professional software
    development, testing, release, deployment and operational practices.
3.  **Technical understanding:** Understand Go, distributed systems,
    architecture, implementation decisions, testing methods and
    engineering trade-offs.

AI will be used extensively to write and modify code, tests,
configuration, scripts and documentation. The goal is not to write code
manually; the goal is to understand, direct, review and validate the
engineering work.

## 2. Guiding principles

### 2.1 Production readiness from the beginning

Professional practices apply from the first release:

-   Git and branching from the first implementation.
-   Automated tests from the first component.
-   Continuous integration from the first pull request.
-   Documentation alongside implementation.
-   Security considerations during architecture and implementation.
-   Structured logging and deliberate error handling.
-   Repeatable build, deployment and release processes.

We will introduce complexity progressively, but we will not ignore
engineering discipline.

### 2.2 AI-assisted implementation

AI may be used to:

-   Write and modify Go functions, packages and tests.
-   Create configuration files, database migrations and scripts.
-   Generate CI/CD workflows.
-   Help investigate and debug failures.
-   Review code and suggest improvements.
-   Create and maintain technical documentation.

AI-generated code is not presumed correct because it compiles or its
tests pass. We must understand and independently validate important
behaviour.

### 2.3 Version-driven development

Every version has a defined scope, requirements, design, implementation
plan, tests, acceptance criteria and release process. We will not
advance merely because the code appears to work.

### 2.4 Incremental architecture

We will introduce distributed-systems complexity in stages:

-   One coordinator before multiple coordinators.
-   One worker before a worker cluster.
-   Basic dispatch before advanced scheduling.
-   Heartbeats before advanced failure detection.
-   Persistent state before recovery mechanisms.
-   At-least-once execution before exploring more advanced guarantees.
-   Single-coordinator recovery before consensus and high availability.

### 2.5 Learn through engineering problems

We will deliberately encounter and investigate race conditions,
deadlocks, timeouts, duplicate execution, lost messages, database
inconsistencies, process crashes, resource exhaustion, performance
bottlenecks and deployment failures.

------------------------------------------------------------------------

## 3. Master development lifecycle

The following lifecycle applies to every significant version:

1.  Requirements engineering.
2.  Architecture and technical design.
3.  Development planning.
4.  AI-assisted implementation.
5.  Testing and verification.
6.  Continuous integration.
7.  Release preparation.
8.  Deployment.
9.  Production verification.
10. Retrospective and next-version planning.

The depth of each activity should be appropriate to the version, but the
lifecycle should remain consistent.

------------------------------------------------------------------------

## 4. Requirements engineering

Every version begins with requirements, not code.

### 4.1 Requirements documents

  -----------------------------------------------------------------------
  Document                            Purpose
  ----------------------------------- -----------------------------------
  Product Requirements Document (PRD) What we are building and why

  Functional Requirements             What the system must do

  Non-Functional Requirements (NFRs)  Performance, reliability, security
                                      and scalability expectations

  Use Cases                           How users and components interact
                                      with the system

  Acceptance Criteria                 How we determine whether
                                      requirements are satisfied

  Glossary                            Consistent terminology
  -----------------------------------------------------------------------

### 4.2 Requirements classification

Requirements should cover:

-   Functional behaviour.
-   Performance.
-   Reliability and availability.
-   Security and privacy.
-   Scalability.
-   Maintainability.
-   Compatibility.
-   Operability and supportability.

Requirements must be testable wherever practical. For example, "recover
failed tasks" is too vague on its own. We must define how failure is
detected, what happens to in-flight tasks, how reassignment works, how
duplicate execution is handled and how recovery is measured.

### 4.3 AI involvement

AI can help identify missing requirements, challenge assumptions,
discover edge cases and convert statements into testable acceptance
criteria. Requirements are approved before design and implementation
proceed.

------------------------------------------------------------------------

## 5. Architecture and technical design

We will design the system before asking AI to implement significant
components.

### 5.1 Architecture deliverables

  -----------------------------------------------------------------------
  Deliverable                         Coverage
  ----------------------------------- -----------------------------------
  System context diagram              System boundaries and external
                                      actors

  Container/process diagram           Coordinator, workers, clients and
                                      storage

  Component diagrams                  Internal component responsibilities

  Sequence diagrams                   Runtime interactions and message
                                      flows

  Deployment diagrams                 Processes and machines in each
                                      environment

  Data model                          Jobs, tasks, workers and execution
                                      history

  API specifications                  Request/response contracts

  Protocol specifications             Inter-process communication

  Architecture Decision Records       Important decisions and their
  (ADRs)                              rationale
  -----------------------------------------------------------------------

### 5.2 Architecture Decision Records

Every significant decision should record:

-   Context and problem.
-   Decision.
-   Alternatives considered.
-   Reasons for the decision.
-   Consequences and limitations.
-   Date and status.

Example: begin with a single coordinator and independent worker
processes. This keeps the initial system understandable while leaving
coordinator high availability for a later stage. The resulting single
point of failure must be documented.

### 5.3 Design review

Before implementation, review:

-   Consistency with approved requirements.
-   Component boundaries and responsibilities.
-   Interfaces and dependencies.
-   Failure scenarios.
-   Testability.
-   Security implications.
-   Operational implications.
-   Unnecessary complexity.
-   Alternatives and trade-offs.

------------------------------------------------------------------------

## 6. Development planning and work management

Work will be managed through a version and issue hierarchy.

**Version → Epic → Feature → Issue/Task**

### 6.1 Issue categories

-   Feature.
-   Bug.
-   Technical debt.
-   Refactoring.
-   Testing.
-   Security.
-   Documentation.
-   Infrastructure and operations.

Each issue should include a description, rationale, scope, dependencies,
acceptance criteria and testing requirements.

### 6.2 Definition of Ready

A task is ready when:

-   Its expected behaviour is understood.
-   Its scope is clear.
-   Acceptance criteria exist.
-   Dependencies are identified.
-   Significant design questions are resolved.

### 6.3 Definition of Done

A task is complete when:

-   Implementation is complete.
-   Relevant tests pass.
-   Code review is complete.
-   Required automated checks pass.
-   Documentation is updated.
-   Changes are merged through the agreed workflow.
-   Acceptance criteria are satisfied.

A feature that works locally but has no appropriate tests or
documentation is not considered done.

------------------------------------------------------------------------

## 7. AI-assisted implementation methodology

AI writes most of the code, but implementation remains controlled and
reviewable.

### 7.1 Before implementation

For each feature, establish:

1.  What must be implemented?
2.  Which existing components are affected?
3.  Which interfaces and contracts are involved?
4.  What failure cases must be considered?
5.  Which tests are required?
6.  What must not change?

AI should inspect the repository and relevant project instructions
before proposing modifications.

### 7.2 During implementation

Break work into small, coherent tasks. For example, implement worker
execution through separate tasks:

-   Define worker configuration and lifecycle.
-   Define coordinator communication.
-   Implement task reception.
-   Implement task execution.
-   Implement result reporting.
-   Add error handling and resource cleanup.
-   Add unit and integration tests.
-   Update documentation.

Avoid asking an agent to build an entire subsystem in one unreviewed
change.

### 7.3 After implementation

Review:

-   Correctness and control flow.
-   Package and interface boundaries.
-   Error handling.
-   Concurrency safety.
-   Context cancellation and timeouts.
-   Resource cleanup.
-   Test quality and coverage.
-   Performance implications.
-   Security implications.
-   Documentation.

### 7.4 AI project instructions

Maintain an `AGENTS.md` or equivalent project instruction file. It
should describe:

-   Architecture and package boundaries.
-   Coding and naming standards.
-   Error-handling expectations.
-   Testing requirements.
-   Dependency policies.
-   Security rules.
-   Build and validation commands.
-   Documentation expectations.

AI must not silently change architecture, public APIs, tests or
unrelated files. It must not remove or weaken tests merely to make a
build pass, ignore errors, hardcode credentials or claim checks passed
without running them.

------------------------------------------------------------------------

## 8. Git and source control

Git is used from the first implementation.

### 8.1 Branching model

Use a lightweight GitFlow-inspired approach:

  Branch        Purpose
  ------------- ------------------------------------
  `main`        Production-ready releases
  `develop`     Integration branch
  `feature/*`   New functionality
  `bugfix/*`    Non-urgent bug fixes
  `hotfix/*`    Urgent fixes to a released version
  `release/*`   Release preparation

### 8.2 Pull-request workflow

1.  Create an issue.
2.  Create a branch from the appropriate base.
3.  Implement a focused change with AI assistance.
4.  Run local checks.
5.  Commit with meaningful messages.
6.  Push the branch and open a pull request.
7.  Run CI.
8.  Review the change.
9.  Address review comments.
10. Merge after required checks and approvals.
11. Delete the completed branch.

### 8.3 Git concepts to practise

-   Commits and commit messages.
-   Branching and merging.
-   Rebasing.
-   Merge conflicts.
-   Cherry-picking.
-   Reverting.
-   Tags and release branches.
-   Pull requests and code reviews.
-   Protected branches.
-   History inspection and rollback.

### 8.4 Code review criteria

Review correctness, architecture consistency, maintainability, error
handling, concurrency safety, security, performance, test quality and
documentation. AI may conduct an initial review, but important findings
must be examined independently.

------------------------------------------------------------------------

## 9. Testing methodology

Testing is a collection of complementary techniques. We will select
tests based on risk and behaviour rather than relying on one test type.

### 9.1 Unit testing

Test individual functions and components in isolation.

Examples:

-   Job validation.
-   Task creation.
-   Scheduling decisions.
-   Retry calculations.
-   Lease expiration calculations.
-   Configuration parsing.

Use Go's `testing` package, table-driven tests and test doubles where
appropriate. Additional assertion or mocking libraries should be
justified rather than added automatically.

### 9.2 Integration testing

Test interactions between components, such as:

-   Coordinator and database.
-   Worker and coordinator.
-   API and repository.
-   Scheduler and task queue.

Practise temporary databases, test fixtures, migrations, resource
cleanup and test isolation.

### 9.3 Contract testing

Verify that independently developed components agree on communication
contracts.

Examples:

-   Worker registration.
-   Task assignment.
-   Task result reporting.
-   Heartbeat messages.
-   Error responses.

### 9.4 System testing

Run the complete application as independent processes and test system
behaviour.

Examples:

-   Start coordinator and multiple workers.
-   Submit jobs.
-   Verify task distribution and results.
-   Terminate a worker and examine recovery.
-   Restart components and verify state.

### 9.5 End-to-end testing

Test complete user-visible workflows through public interfaces, such as:

`Submit job → Track progress → Retrieve result`

### 9.6 Regression testing

When a bug is found, add a regression test where practical. The test
should demonstrate the original failure and protect against recurrence.

### 9.7 Concurrency testing

Test:

-   Data races.
-   Concurrent submissions and result reporting.
-   Shared-state access.
-   Goroutine leaks.
-   Deadlocks.
-   Shutdown races.
-   Cancellation and timeout behaviour.

Useful Go commands:

``` bash
go test ./...
go test -race ./...
go test -count=20 ./...
go test -cover ./...
go vet ./...
```

### 9.8 Fault-injection testing

Deliberately simulate:

-   Worker crashes.
-   Coordinator crashes.
-   Network disconnections.
-   Delayed, lost and duplicated messages.
-   Database failures.
-   Worker restarts.
-   Partial execution.
-   Simultaneous failures.

Measure recovery behaviour, not merely whether an error was returned.

### 9.9 Performance testing

  Test               Purpose
  ------------------ -------------------------------------------
  Benchmark          Measure individual operations
  Load test          Measure expected workload behaviour
  Stress test        Push beyond expected limits
  Soak test          Run for an extended period
  Spike test         Examine sudden workload increases
  Scalability test   Understand capacity as resources increase

Measure throughput, average latency, p50/p95/p99 latency, queue depth,
CPU, memory, worker utilisation, failure rate and recovery time.

### 9.10 Security testing

Include static analysis, dependency vulnerability scanning,
authentication and authorization tests, input validation, rate-limit
tests, secrets scanning and network-security checks.

### 9.11 Test strategy and traceability

Maintain a test strategy and a test matrix mapping requirements to test
cases and results. Not every test belongs in every pipeline: fast tests
should run frequently, while expensive fault, soak and performance tests
can run on scheduled or release pipelines.

------------------------------------------------------------------------

## 10. Continuous Integration (CI)

CI will be introduced in the first release. Pull requests should
automatically run appropriate checks.

A baseline pipeline should include:

1.  Checkout repository.
2.  Set up the required Go version.
3.  Verify dependencies.
4.  Check formatting.
5.  Run static analysis and linting.
6.  Run unit tests.
7.  Run race detection where appropriate.
8.  Run integration tests.
9.  Build binaries.
10. Run security and dependency checks.
11. Publish test results and build artifacts.

### CI concepts to learn

-   GitHub Actions.
-   Workflow YAML.
-   Jobs and steps.
-   Environment variables and secrets.
-   Build matrices.
-   Dependency caching.
-   Test reports and artifacts.
-   Pipeline failures and debugging.
-   Branch protection and quality gates.

We will distinguish fast pull-request checks from more expensive
scheduled and release checks.

------------------------------------------------------------------------

## 11. Continuous Delivery and Deployment (CD)

We will distinguish:

-   **Continuous delivery:** The software is kept in a deployable state;
    production deployment requires approval.
-   **Continuous deployment:** Qualifying changes are automatically
    deployed.

Initially, we will use continuous delivery with explicit release
approval.

### 11.1 Deployment progression

  Stage   Target
  ------- ------------------------------------
  1       Local development
  2       Multiple local processes
  3       Docker-based environment
  4       Remote test or staging environment
  5       Production-like environment
  6       Production deployment

### 11.2 CD activities

-   Build reproducible binaries.
-   Package applications.
-   Build and publish container images when introduced.
-   Manage environment-specific configuration.
-   Apply database migrations safely.
-   Deploy coordinator and workers.
-   Run smoke tests and readiness checks.
-   Verify deployment.
-   Roll back failed releases.
-   Maintain deployment records.

We will learn rolling and blue-green deployment when the architecture
supports them. We will also practise coordinator/worker version
compatibility and independent worker upgrades.

------------------------------------------------------------------------

## 12. Security engineering

Security is considered throughout design, implementation, testing and
operations.

Areas include:

  Area                 Practices
  -------------------- ------------------------------------------
  Authentication       Verify clients and workers
  Authorization        Control who can submit and manage jobs
  Transport security   TLS and secure communication
  Secrets              Secure credential handling
  Validation           Reject malformed and malicious input
  Resource limits      Prevent resource exhaustion
  API security         Rate limiting and abuse protection
  Dependencies         Vulnerability management
  Supply chain         Trusted builds and dependency provenance
  Auditability         Record security-relevant actions

We will threat-model the system before exposing it beyond a trusted
local environment. Task execution must not permit arbitrary code
execution, uncontrolled file access or unbounded resource consumption.

------------------------------------------------------------------------

## 13. Observability and operational engineering

A distributed system must be able to explain its own behaviour.

### 13.1 Logging

Learn structured logs, log levels, correlation IDs, request IDs and
consistent job, task and worker identifiers.

### 13.2 Metrics

Progressively expose:

-   Jobs submitted.
-   Tasks queued, executing, completed and failed.
-   Retry counts.
-   Queue waiting time.
-   Worker availability and utilisation.
-   Task execution latency.
-   Coordinator and worker resource consumption.

### 13.3 Distributed tracing

Learn OpenTelemetry and trace execution across:

`Client → Coordinator → Scheduler → Worker → Coordinator → Database`

### 13.4 Operational practices

Practise:

-   Health and readiness checks.
-   Graceful shutdown.
-   Backups and restoration.
-   Database migrations.
-   Configuration management.
-   Log and trace investigation.
-   Incident response.
-   Runbook execution.
-   Rollback.

Define service-level indicators and objectives (SLIs/SLOs) once
sufficient measurements and operational expectations are available.

------------------------------------------------------------------------

## 14. Version management and release methodology

Every version follows a repeatable lifecycle.

``` text
Define scope
    ↓
Approve requirements
    ↓
Review architecture and design
    ↓
Create epics and issues
    ↓
Implement
    ↓
Review code and run CI
    ↓
Complete integration and system tests
    ↓
Run applicable security and performance tests
    ↓
Prepare release candidate
    ↓
Acceptance testing
    ↓
Release approval
    ↓
Tag and publish
    ↓
Deploy and verify
    ↓
Retrospective
    ↓
Plan next version
```

### 14.1 Release gates

  Gate           Required outcome
  -------------- -------------------------------------------------
  Requirements   Scope and acceptance criteria approved
  Design         Architecture and important decisions reviewed
  Development    Planned implementation completed
  Quality        Required tests and automated checks pass
  Release        Release candidate satisfies acceptance criteria
  Deployment     Deployment and rollback procedures verified
  Closure        Documentation and retrospective completed

### 14.2 Semantic versioning

Use `MAJOR.MINOR.PATCH`.

Examples:

-   `v0.1.0` --- Initial distributed execution.
-   `v0.2.0` --- Multiple workers.
-   `v0.2.1` --- Bug fix.
-   `v0.3.0` --- Worker health monitoring.
-   `v1.0.0` --- First stable production release.

During `0.x` development, interfaces may change, but compatibility
changes must still be documented.

### 14.3 Release documentation

Every release should record:

-   Version and date.
-   Features added.
-   Bugs fixed.
-   Known limitations.
-   Breaking changes.
-   Database migration changes.
-   Deployment instructions.
-   Test results.
-   Upgrade and rollback instructions.

------------------------------------------------------------------------

## 15. Performance and scalability engineering

Performance is measured throughout development, not left until the end.

### 15.1 Establish baselines

For example, measure the same workload with one, two, four and eight
workers. Examine whether additional workers improve throughput and at
what point coordinator, database or network bottlenecks appear.

### 15.2 Investigate bottlenecks

Potential bottlenecks include:

-   Coordinator CPU.
-   Database writes and connection limits.
-   Network communication.
-   Scheduling overhead.
-   Worker resource limits.
-   Lock contention.
-   Goroutine creation and management.
-   Queue contention.

### 15.3 Go performance tools

Learn CPU and memory profiling, allocation analysis, goroutine and mutex
profiling, benchmarking and execution tracing.

``` bash
go test -bench=. -benchmem ./...
go test -cpuprofile=cpu.prof ./...
go test -memprofile=mem.prof ./...
go tool pprof
```

### 15.4 Scalability experiments

Distinguish number of jobs, number of tasks, worker count, concurrent
executions, submission rate and completion rate.

The eventual goal is to demonstrate thousands of tasks across multiple
independent worker processes, with measured performance and documented
limitations.

------------------------------------------------------------------------

## 16. Documentation and knowledge management

Documentation is a project deliverable.

Suggested repository structure:

``` text
docs/
├── product/
│   ├── PRD.md
│   ├── requirements.md
│   └── use-cases.md
├── architecture/
│   ├── overview.md
│   ├── components.md
│   ├── protocols.md
│   └── diagrams/
├── decisions/
│   ├── ADR-001.md
│   └── ADR-002.md
├── development/
│   ├── methodology.md
│   ├── coding-standards.md
│   ├── testing-strategy.md
│   └── contributing.md
├── operations/
│   ├── deployment.md
│   ├── monitoring.md
│   ├── backup-restore.md
│   └── runbooks/
└── releases/
    ├── v0.1.0.md
    └── v0.2.0.md
```

Maintain a separate learning log recording:

-   What was learned.
-   The problem a concept solves.
-   Important concepts and terminology.
-   Decisions and alternatives.
-   Experiments and observations.
-   Questions still unresolved.

------------------------------------------------------------------------

## 17. Learning methodology

We must not confuse successful AI implementation with successful
learning.

For every significant feature, follow this cycle:

1.  **Conceptual learning:** Understand the underlying computer science
    and engineering concepts.
2.  **Design understanding:** Understand how the concept applies to our
    architecture and what alternatives exist.
3.  **AI-assisted implementation:** Use AI to write the code, tests and
    supporting files.
4.  **Code walkthrough:** Understand packages, functions, control flow,
    data structures and concurrency.
5.  **Testing and experimentation:** Run tests, introduce failures and
    observe behaviour.
6.  **Knowledge validation:** Explain the implementation and answer
    design and debugging questions.

For example, when implementing task leasing, learn what a lease is, how
it differs from a lock, how expiration works, what happens when an old
worker reports a result, how fencing tokens help, which race conditions
are possible and how to test them.

Then implement, inspect, test and deliberately challenge the
implementation.

------------------------------------------------------------------------

## 18. Engineering standards and quality controls

  Area            Standard or practice
  --------------- -----------------------------------------------
  Go code         `gofmt`, `go vet`, appropriate linting
  Dependencies    Controlled dependencies and version updates
  Errors          Explicit handling and useful context
  Concurrency     Race detection and lifecycle management
  APIs            Versioned and documented contracts
  Database        Versioned migrations and backup strategy
  Tests           Repeatable, isolated and meaningful tests
  Security        Threat modelling and dependency scanning
  Git             Small, reviewable commits
  CI              Automated quality gates
  CD              Reproducible builds and controlled deployment
  Observability   Structured logs, metrics and traces
  Releases        Versioned, documented and verifiable

We will use relevant industry guidance, including Twelve-Factor App
principles where applicable, OWASP guidance, Semantic Versioning and
OpenTelemetry conventions. Tools and dependencies must have a clear
justification.

------------------------------------------------------------------------

## 19. Working rhythm

For each significant feature or milestone:

1.  Discuss the engineering topic.
2.  Understand concepts and alternatives.
3.  Finalise the design.
4.  Define implementation tasks.
5.  Use AI to implement.
6.  Inspect and understand generated code.
7.  Run relevant tests.
8.  Investigate failures.
9.  Review and merge changes.
10. Update documentation and learning notes.

### 19.1 Milestone retrospective

At the end of each milestone, ask:

-   What did we accomplish?
-   What did we learn?
-   What went wrong?
-   Which architectural decisions should be revisited?
-   Are there quality gaps?
-   What technical debt was introduced?
-   Are we ready for the next milestone?

------------------------------------------------------------------------

## 20. Version roadmap and engineering learning

  -----------------------------------------------------------------------
  Version                             Primary engineering learning
  ----------------------------------- -----------------------------------
  `v0.1.0`                            Repository setup, Go architecture,
                                      APIs, unit/integration testing and
                                      basic CI

  `v0.2.0`                            Multi-process communication,
                                      concurrency, contract and system
                                      testing

  `v0.3.0`                            Heartbeats, failure detection,
                                      lifecycle management and fault
                                      testing

  `v0.4.0`                            Scheduling algorithms, resource
                                      management and performance

  `v0.5.0`                            Persistence, transactions, leases,
                                      retries, recovery and consistency

  `v0.6.0`                            Observability, metrics, tracing,
                                      dashboards and operations

  `v0.7.0`                            Threat modelling, authentication,
                                      authorization and security testing

  `v0.8.0`                            Coordinator recovery, durability,
                                      backups and restoration

  `v0.9.0`                            Load, stress, soak, scalability and
                                      resilience testing

  `v1.0.0`                            Production deployment, release
                                      engineering, rollback and
                                      operational readiness
  -----------------------------------------------------------------------

Git, testing, documentation, code review and CI apply throughout; they
are not postponed until their associated milestone.

------------------------------------------------------------------------

## 21. Production readiness

A working distributed system is not automatically a production-ready
distributed system.

Before `v1.0.0`, we should be able to demonstrate the following.

### Functionality

-   Jobs and tasks execute correctly.
-   Multiple independent workers operate correctly.
-   Results and execution history are available.

### Reliability

-   Worker failures are detected and recovered.
-   Coordinator recovery is tested.
-   Duplicate execution is handled safely.
-   Persistent state survives restarts.

### Testing

-   Unit, integration and system tests pass.
-   Concurrency and race tests pass.
-   Fault-injection scenarios are tested.
-   Performance targets are demonstrated.

### Security

-   Authentication and authorization work.
-   Secrets are protected.
-   Inputs and resources are controlled.
-   Dependency and security scans are reviewed.

### Operations

-   Logs, metrics and traces are available.
-   Health and readiness checks work.
-   Backup and restore are demonstrated.
-   Deployment and rollback are documented.

### Engineering

-   CI/CD pipelines work.
-   The release process is repeatable.
-   Architecture and API documentation are current.
-   Known limitations and operational risks are documented.

We will define measurable thresholds for throughput, latency, recovery
time, availability and resource consumption before final acceptance
testing. We will not invent arbitrary targets before establishing the
architecture and baseline.

------------------------------------------------------------------------

## 22. Roles and responsibilities

### AI assistant

Acts as an architecture and engineering partner, Go implementation
assistant, testing guide, reviewer, debugging assistant and DevOps
mentor.

### Project owner

Approves requirements, architectural decisions, scope, acceptance
criteria and releases. Understands the system and takes responsibility
for validating the resulting software.

### Three parallel tracks

1.  **Product development:** Build and release the distributed execution
    platform.
2.  **Engineering practices:** Learn Git, testing, reviews, CI/CD,
    security, deployment, monitoring and operations.
3.  **Technical understanding:** Learn Go, concurrency, distributed
    systems, databases, networking, algorithms and architecture.

The three tracks progress together. A feature is not considered fully
complete until its implementation, relevant engineering practices and
learning objectives have been addressed.

------------------------------------------------------------------------

## 23. Immediate project sequence

After adopting this methodology, proceed in this order:

1.  **Project Charter:** Objectives, boundaries, stakeholders and
    success criteria.
2.  **PRD v1.0:** Product requirements and use cases.
3.  **NFR specification:** Measurable reliability, performance, security
    and scalability requirements.
4.  **MVP definition:** Exact scope of `v0.1.0`.
5.  **Architecture design:** System and component architecture.
6.  **Technical design:** APIs, protocols, database and interfaces.
7.  **Development environment:** Repository, GitHub, Go, AI tooling and
    development standards.
8.  **Implementation planning:** Epics, issues and acceptance criteria
    for `v0.1.0`.

## 24. Methodology governance

This document is the baseline development framework for the project.

-   Keep it in the repository as `DEVELOPMENT_METHODOLOGY.md`.
-   Review it at major release boundaries.
-   Change it when experience reveals a meaningful improvement.
-   Record significant methodology changes through documented decisions.
-   Do not change the methodology casually to bypass quality gates or
    avoid difficult engineering work.

**Core principle:** AI assists with implementation; the project owner
must understand the architecture, engineering decisions, tests,
deployment and operation of the system.
