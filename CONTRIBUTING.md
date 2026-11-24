# Contributing to Distributed Job Engine

## 1. Development Principles

All development must follow:

- DEVELOPMENT_METHODOLOGY.md
- AGENTS.md
- Approved project requirements and architecture decisions

Changes should be small, understandable, testable and reviewable.

## 2. Branching Strategy

Permanent branches:

- main: Stable, release-ready code.
- develop: Integration branch for ongoing development.

Temporary branches:

- feature/<name>: New functionality.
- bugfix/<name>: Bug fixes.
- hotfix/<name>: Urgent fixes to released versions.
- release/<version>: Release preparation.

## 3. Feature Development Workflow

1. Create or identify a GitHub issue.
2. Confirm requirements and acceptance criteria.
3. Create a feature branch from develop.
4. Inspect the existing implementation.
5. Prepare an implementation plan.
6. Use AI assistance to implement the change.
7. Add or update tests.
8. Run relevant automated checks.
9. Review generated code and documentation.
10. Commit changes using meaningful commit messages.
11. Push the feature branch.
12. Open a pull request against develop.
13. Review CI results and code changes.
14. Address review comments.
15. Merge after all required checks pass.

## 4. Commit Message Convention

Use Conventional Commits where practical.

Examples:

- feat: add worker registration
- fix: handle expired task leases
- test: add scheduler integration tests
- docs: document worker communication protocol
- refactor: simplify task repository
- chore: update development dependencies
- ci: add Go test workflow

## 5. Pull Request Requirements

Every pull request should contain:

- Summary of the change.
- Reason for the change.
- Related issue.
- Implementation details.
- Tests added or modified.
- Test commands and actual results.
- Documentation changes.
- Known limitations or risks.

Pull requests should be focused and reasonably small.

## 6. Code Review

Review changes for:

- Correctness.
- Architecture consistency.
- Maintainability.
- Error handling.
- Concurrency safety.
- Security.
- Performance.
- Test quality.
- Documentation.

AI-assisted reviews may be used, but findings must be evaluated rather than accepted blindly.

## 7. Testing

Run the relevant checks before opening a pull request.

Common Go commands:

    go test ./...
    go test -race ./...
    go vet ./...

Additional integration, system, security and performance tests
will be introduced as required by each project version.

## 8. Merging

- Feature branches merge into develop.
- Release branches are used for release preparation.
- Approved releases merge into main.
- Urgent production fixes use hotfix branches.
- Do not commit directly to main.

## 9. Definition of Done

A change is complete when:

- Implementation is complete.
- Relevant tests pass.
- Code review is complete.
- Required CI checks pass.
- Documentation is updated.
- Acceptance criteria are satisfied.
- Changes are merged through the approved workflow.
