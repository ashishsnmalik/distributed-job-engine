# AI Development Instructions

## 1. Project Overview

Project: Distributed Job Engine
Language: Go
Repository: distributed-job-engine

Build a general-purpose distributed job execution platform.

The primary objective is to learn and implement production-grade distributed systems engineering.

Task processing must remain deliberately simple. Engineering effort should focus on distributed execution, coordination, scheduling, reliability and fault recovery.

## 2. Development Philosophy

- Follow DEVELOPMENT_METHODOLOGY.md.
- Work incrementally through formal versions.
- Do not implement future-version features prematurely.
- Understand existing architecture before proposing changes.
- Prefer simple, maintainable solutions over unnecessary complexity.
- Never silently change approved architectural decisions.
- Explain important implementation and design decisions.

## 3. AI-Assisted Development Rules

- AI may generate and modify code, tests, scripts and documentation.
- Inspect relevant existing files before making changes.
- Work on one coherent feature or task at a time.
- Do not modify unrelated files.
- Do not overwrite existing work without justification.
- Do not introduce dependencies without explaining why.
- Do not claim tests or checks passed unless they were actually executed.
- Never remove or weaken tests simply to make a build pass.
- Explain significant changes and their consequences.

## 4. Architecture Rules

- Keep coordinator, worker, API, scheduler and storage responsibilities separate.
- Workers must be independent processes.
- Components must communicate through explicit interfaces and network protocols.
- Do not use shared process memory between workers and coordinator.
- Keep task executors independent of scheduling logic.
- Make components independently testable.
- Record significant architectural decisions as ADRs.
- Avoid premature distributed consensus and high availability.

## 5. Go Engineering Standards

- Follow standard Go project conventions.
- Format code using gofmt.
- Use meaningful package, type and function names.
- Handle errors explicitly.
- Avoid ignored errors.
- Use context for cancellation and deadlines where appropriate.
- Manage goroutine and resource lifecycles carefully.
- Avoid data races and uncontrolled shared state.
- Keep interfaces small and purposeful.
- Document exported declarations where appropriate.
- Avoid unnecessary abstractions.

## 6. Testing Requirements

- Add or update tests for relevant behaviour.
- Prefer table-driven tests where appropriate.
- Test failure paths, not just successful execution.
- Test concurrency-sensitive behaviour.
- Include regression tests for fixed bugs.
- Do not use mocks when a realistic integration test is more appropriate.
- Keep tests deterministic and independently repeatable.
- Explain what each significant test verifies.

Relevant validation commands include:

    go test ./...
    go test -race ./...
    go vet ./...

## 7. Security Requirements

- Never hardcode credentials or secrets.
- Validate external input.
- Apply appropriate timeouts and resource limits.
- Consider authentication and authorization boundaries.
- Avoid unsafe file and process operations.
- Review dependencies before introducing them.
- Consider security implications of all network-facing functionality.

## 8. Git and Change Management

- Follow the branching strategy in CONTRIBUTING.md.
- Do not commit directly to main.
- Do not force-push shared branches.
- Keep changes focused and reviewable.
- Use meaningful commit messages.
- Do not bypass required CI checks.
- Do not merge changes without reviewing them.

## 9. Documentation

- Update documentation when behaviour or architecture changes.
- Maintain architecture decision records.
- Document API and protocol changes.
- Update test documentation when testing strategy changes.
- Record release changes and known limitations.

## 10. Implementation Workflow

For each task:

1. Understand the requirement.
2. Inspect the existing repository.
3. Identify affected components.
4. Propose an implementation plan.
5. Identify risks and failure scenarios.
6. Implement the smallest coherent change.
7. Add or update tests.
8. Run relevant checks.
9. Explain the changes.
10. Report test results and remaining limitations.

## 11. Important Constraint

The project owner must understand the architecture, implementation,
testing methodology and engineering decisions.

Generating code successfully does not mean the engineering task
or learning objective is complete.
