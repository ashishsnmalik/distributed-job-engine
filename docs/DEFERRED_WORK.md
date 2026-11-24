# Deferred Work Register — Distributed Job Engine

**Document Version:** 1.0  
**Status:** Active Register  
**Project:** distributed-job-engine  
**Last Updated:** 25 November 2026

---

## 1. Purpose

This document records features, architectural capabilities and engineering
tasks that have deliberately been postponed.

The purpose is to ensure that:

- Important ideas are not forgotten.
- Deferred work is distinguishable from rejected requirements.
- Reasons for deferral are documented.
- Dependencies and prerequisites are understood.
- Deferred items are reconsidered at appropriate project milestones.
- Scope decisions remain visible throughout development.

Deferring a feature does not mean that it is permanently excluded.

## 2. Deferral Policy

Every deferred item should contain:

- A unique identifier.
- A description of the feature or work.
- The reason for deferral.
- Relevant dependencies or prerequisites.
- A condition for reconsideration.
- A proposed release or development phase, where known.
- A current status.

Deferred items must be reviewed:

1. During release planning.
2. Before major architectural decisions.
3. At release boundaries.
4. When a new requirement makes a deferred item necessary.

Items should not be implemented merely because they appear in this
register. They must first be reviewed and prioritised.

## 3. Deferred Items

### DW-001 — Multiple Coordinators and High Availability

**Category:** Distributed Architecture  
**Status:** Deferred  
**Proposed timing:** Post-v1.0

**Description**

Support multiple coordinator instances to avoid a single coordinator
being a single point of failure.

Potential approaches include:

- Active-passive coordinator architecture.
- Active-active coordinator architecture.
- Leader election.
- Coordinator failover.
- Shared or replicated durable state.

**Reason for deferral**

The initial project should establish correct job execution,
multi-worker coordination, persistence and recovery before introducing
the additional complexity of distributed coordinator coordination.

**Dependencies and prerequisites**

- Stable single-coordinator architecture.
- Durable and recoverable coordinator state.
- Well-defined task ownership and execution semantics.
- Reliable worker registration and failure detection.

**Reconsider when**

The single-coordinator implementation is stable and coordinator
availability becomes a specific architectural requirement.

---

### DW-002 — Leader Election and Consensus Protocols

**Category:** Distributed Architecture  
**Status:** Deferred  
**Proposed timing:** Post-v1.0

**Description**

Introduce mechanisms to elect an active coordinator and prevent
multiple coordinators from simultaneously making conflicting decisions.

Potential topics include:

- Leader election.
- Distributed leases.
- Fencing tokens.
- Split-brain prevention.
- Consensus protocols such as Raft.

**Reason for deferral**

These mechanisms are unnecessary for the initial single-coordinator
architecture and would introduce substantial distributed systems
complexity prematurely.

**Dependencies and prerequisites**

- Multiple-coordinator architecture.
- Defined coordinator ownership model.
- Durable shared or replicated metadata.
- Clear failure detection and recovery semantics.

**Reconsider when**

Multiple coordinators and high availability become an approved
architectural objective.

---

### DW-003 — Active-Active Coordinator Architecture

**Category:** Distributed Architecture and Scalability  
**Status:** Deferred  
**Proposed timing:** Post-v1.0; subject to evaluation

**Description**

Allow multiple coordinators to actively accept and manage work
simultaneously.

Potential approaches include workload partitioning and distributed
coordination.

**Reason for deferral**

Active-active coordination introduces additional challenges around
ownership, consistency, duplicate scheduling and concurrent state
modification.

An active-passive architecture may provide sufficient availability
for the initial high-availability milestone.

**Dependencies and prerequisites**

- Stable multi-coordinator architecture.
- Defined ownership and partitioning strategy.
- Reliable consistency and conflict-handling mechanisms.

**Reconsider when**

Performance or availability requirements demonstrate a need for
active-active coordination.

---

### DW-004 — Dynamic Executor Loading and Hot-Swapping

**Category:** Extensibility  
**Status:** Deferred  
**Proposed timing:** After the initial executor architecture is stable

**Description**

Allow executors to be introduced, updated or replaced dynamically
without restarting workers.

**Initial alternative**

Register executors using Go interfaces when workers start.

**Reason for deferral**

Startup-time registration provides modularity without introducing
the operational and compatibility complexity of dynamic loading.

**Dependencies and prerequisites**

- Stable executor interface.
- Executor versioning and compatibility rules.
- Defined behaviour for updating executors used by running tasks.

**Reconsider when**

There is a demonstrated need to add or update executor implementations
without restarting workers.

---

### DW-005 — Separate Scheduler Service

**Category:** Architecture and Modularity  
**Status:** Deferred  
**Proposed timing:** Revisit after initial scheduling implementation

**Description**

Extract the scheduler from the coordinator into an independent service.

**Initial alternative**

Keep scheduling as a logical component within the coordinator,
with a well-defined internal interface.

**Reason for deferral**

A separate service would introduce additional communication,
deployment and operational complexity.

**Dependencies and prerequisites**

- Stable scheduling responsibilities.
- Clearly defined scheduler interfaces.
- Evidence that independent deployment or scaling is beneficial.

**Reconsider when**

The scheduler requires independent scaling, deployment or failure
isolation.

---

### DW-006 — Web-Based Operational Dashboard

**Category:** Operations and Observability  
**Status:** Deferred  
**Proposed timing:** After core observability is established

**Description**

Develop a web interface for operators to:

- View coordinator and worker health.
- Inspect jobs and tasks.
- View execution history.
- Monitor system metrics.
- Investigate failures.

**Initial alternative**

Use structured logs, metrics, command-line tools and existing
monitoring solutions.

**Reason for deferral**

The primary objective is distributed systems engineering rather than
frontend development. Operational visibility can initially be achieved
without building a custom dashboard.

**Dependencies and prerequisites**

- Stable operational APIs or metrics interfaces.
- Defined observability model.
- Reliable job and worker state reporting.

**Reconsider when**

A dashboard provides meaningful operational value beyond existing
monitoring and command-line tools.

---

### DW-007 — Advanced Resource-Aware Worker Scheduling

**Category:** Scheduling and Resource Management  
**Status:** Deferred  
**Proposed timing:** After basic worker capacity scheduling

**Description**

Introduce advanced scheduling based on resource availability and
task requirements.

Potential capabilities include:

- CPU availability.
- Memory availability.
- Executor-specific concurrency limits.
- Resource reservations.
- Resource-aware worker selection.
- Resource quotas.

**Initial alternative**

Use configured maximum concurrent task slots and advertised
executor capabilities.

**Reason for deferral**

Basic task-slot capacity is sufficient to establish worker
registration, task distribution and concurrency.

**Dependencies and prerequisites**

- Stable worker capacity reporting.
- Defined task resource requirements.
- Reliable resource utilisation measurements.

**Reconsider when**

The basic scheduling model is stable and resource contention or
workload diversity justifies more advanced scheduling.

---

## 4. Explicitly Not Deferred

The following capabilities are mandatory product requirements.
They must not be mistaken for optional future enhancements.

| Capability | Requirement |
|---|---|
| Job cancellation | Mandatory; cooperative cancellation initially |
| Multiple workers | Core platform capability |
| Worker registration | Required |
| Worker capacity reporting | Required, initially task-slot based |
| Error handling | Required from the beginning |
| Persistent job/task state | Required as defined by release scope |
| Crash recovery | Core reliability objective, introduced incrementally |
| Graceful shutdown | Required |
| Automated testing | Required from the beginning |
| CI/CD | Required engineering objective |
| Deployment and operational documentation | Required engineering objective |
| Pluggable executor architecture | Required architectural objective |

The implementation timing of individual capabilities must be established
through release planning and the PRD.

## 5. Review History

| Date | Change |
|---|---|
| 25 Nov 2026 | Initial register created |
| 25 Nov 2026 | Recorded coordinator HA, consensus, dynamic executors, separate scheduler, dashboard and advanced resource scheduling as deferred |

## 6. Register Maintenance

Whenever a feature or engineering task is deferred:

1. Add a new entry with a unique ID.
2. Explain why it is deferred.
3. Identify dependencies and prerequisites.
4. Define when it should be reconsidered.
5. Identify a target release or phase if known.
6. Update the review history.

When an item is approved for implementation, mark it as **Planned** and
reference the relevant release or issue.

When completed, mark it as **Completed** and reference the relevant
implementation or release.

When permanently rejected, mark it as **Rejected** and document why.

---

**End of Document**
