# Decision Log — Distributed Job Engine

**Project:** distributed-job-engine  
**Purpose:** Chronological record of important project and architectural decisions  
**Timestamp convention:** Local time in IST (UTC+05:30)

---

## Decision Recording Rules

1. Record every meaningful product, architecture, technology or process decision.
2. Give each decision a unique sequential ID (`DEC-001`, `DEC-002`, etc.).
3. Record the date and time when the decision is made.
4. State the decision clearly and briefly.
5. Include the reasoning behind the decision.
6. If a decision is later changed, add a new entry referencing the earlier decision. Do not silently rewrite history.
7. Link to a detailed Architecture Decision Record (ADR) when a decision warrants a separate document.

Use this format:

### DEC-XXX — Short decision title

- **Timestamp:** YYYY-MM-DD HH:MM:SS IST
- **Decision:** What was decided.
- **Reasoning:** Why it was decided.
- **Related documents:** Relevant project documents, if any.

---

## Initial Decisions

### DEC-001 — Project focus

- **Timestamp:** 2026-11-24 — time not recorded
- **Decision:** Build a general-purpose distributed job execution platform. Keep job-processing logic deliberately simple and focus engineering effort on distributed systems.
- **Reasoning:** The primary learning objective is distributed computing and professional systems engineering, rather than data transformation or complex application-level processing.
- **Related documents:** `docs/PROJECT_CHARTER.md`

### DEC-002 — Full professional software development lifecycle

- **Timestamp:** 2026-11-24 — time not recorded
- **Decision:** Treat the complete professional software development lifecycle as an equally important project objective.
- **Reasoning:** The project should provide practical experience in requirements, architecture, implementation, error handling, testing, Git workflows, CI/CD, deployment, production operations, monitoring, troubleshooting and maintenance.
- **Related documents:** `DEVELOPMENT_METHODOLOGY.md`, `docs/PROJECT_CHARTER.md`

### DEC-003 — Modular and pluggable architecture

- **Timestamp:** 2026-11-24 — time not recorded
- **Decision:** Design the platform so that major components and job executors can be extended or replaced with minimal impact on unrelated components.
- **Reasoning:** Extensibility and maintainability are core engineering objectives. Component boundaries and interfaces should support future evolution.
- **Related documents:** `AGENTS.md`, `docs/PROJECT_CHARTER.md`

### DEC-004 — Single coordinator initially

- **Timestamp:** 2026-11-24 — time not recorded
- **Decision:** Start with a single coordinator. Keep the architecture open to multiple coordinators in the future.
- **Reasoning:** Establish correct execution, persistence, worker coordination and recovery before introducing high-availability coordination complexity.
- **Related documents:** `docs/PROJECT_CHARTER.md`, `docs/product/PRD.md`

### DEC-005 — Independent worker processes

- **Timestamp:** 2026-11-24 — time not recorded
- **Decision:** Workers will run as independent processes and must not depend on shared memory with the coordinator or other workers.
- **Reasoning:** This establishes realistic process and network boundaries and prepares the platform for deployment across multiple machines.
- **Related documents:** `docs/PROJECT_CHARTER.md`, `docs/product/PRD.md`

### DEC-006 — Executors separated from coordination

- **Timestamp:** 2026-11-25 — time not recorded
- **Decision:** Job executors will implement job-specific operations and remain independent of scheduling, worker registration and distributed coordination.
- **Reasoning:** New job types should be added without modifying the coordinator's scheduling logic.
- **Related documents:** `docs/product/PRD.md`, `docs/DEFERRED_WORK.md`

### DEC-007 — Startup-time executor registration

- **Timestamp:** 2026-11-25 — time not recorded
- **Decision:** Initially register executors with workers at startup using Go interfaces. Defer dynamic loading and hot-swapping.
- **Reasoning:** This provides a pluggable architecture without introducing unnecessary runtime loading and compatibility complexity.
- **Related documents:** `docs/product/PRD.md`, `docs/DEFERRED_WORK.md`

### DEC-008 — Scheduler remains within coordinator initially

- **Timestamp:** 2026-11-25 — time not recorded
- **Decision:** Treat the scheduler as a logical component within the coordinator rather than a separate service.
- **Reasoning:** Maintain clear internal boundaries while avoiding additional deployment and communication complexity. Revisit separation if independent scaling or deployment becomes necessary.
- **Related documents:** `docs/product/PRD.md`, `docs/DEFERRED_WORK.md`

### DEC-009 — Worker capacity based on task slots initially

- **Timestamp:** 2026-11-25 — time not recorded
- **Decision:** Initially represent worker capacity using maximum concurrent task slots, occupied slots and available slots. Workers will also advertise supported executor capabilities.
- **Reasoning:** A simple capacity model supports basic scheduling and concurrency without requiring advanced CPU and memory resource management.
- **Related documents:** `docs/product/PRD.md`, `docs/DEFERRED_WORK.md`

### DEC-010 — Job cancellation is mandatory

- **Timestamp:** 2026-11-25 — time not recorded
- **Decision:** Job cancellation is a mandatory platform capability, not an optional enhancement.
- **Reasoning:** Clients must be able to cancel queued and running jobs, and the platform must track and report cancellation outcomes.
- **Related documents:** `docs/product/PRD.md`

### DEC-011 — Cooperative cancellation initially

- **Timestamp:** 2026-11-25 — time not recorded
- **Decision:** Implement cancellation initially through cooperative cancellation using Go's `context.Context`, propagated from coordinator to worker and executor.
- **Reasoning:** Cooperative cancellation provides controlled resource cleanup and avoids assuming arbitrary Go code can be safely terminated. Forceful termination through isolated task processes can be evaluated later.
- **Related documents:** `docs/product/PRD.md`, `docs/DEFERRED_WORK.md`

### DEC-012 — Maintain a deferred work register

- **Timestamp:** 2026-11-25 — time not recorded
- **Decision:** Maintain `docs/DEFERRED_WORK.md` as a living register of postponed features and engineering work.
- **Reasoning:** Deferred items must retain their rationale, prerequisites and reconsideration criteria so they are not forgotten or accidentally treated as rejected.
- **Related documents:** `docs/DEFERRED_WORK.md`

### DEC-013 — Maintain a chronological decision log

- **Timestamp:** GENERATED_AT
- **Decision:** Maintain this file as the chronological record of meaningful project decisions, including timestamps and concise reasoning.
- **Reasoning:** Preserve the history and rationale of project decisions, make changes traceable and avoid repeatedly revisiting settled questions without understanding their context.
- **Related documents:** `docs/DECISION_LOG.md`

---

## Future Entries

Append new decisions below this line, using the next available ID.
