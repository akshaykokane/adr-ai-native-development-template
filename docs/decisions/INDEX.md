# Decision Index

Lightweight catalog of architectural decisions. Full reasoning lives in each ADR; do not duplicate it here.
Agents: read this first, then open ADRs whose **Applies To** matches the files you are changing.

| ID | Title | Status | Applies To | Supersedes |
|---|---|---|---|---|
| [ADR-001](ADR-001-cpu-processing.md) | Use CPU-based processing | Accepted | `services/document-processing/**`, `infrastructure/document-processing/**` | None |
| [ADR-002](ADR-002-storage-strategy.md) | Object storage for raw documents, relational DB for metadata | Accepted | `services/storage/**`, `infrastructure/storage/**` | None |
| [ADR-003](ADR-003-event-driven-processing.md) | Event-driven document processing | Accepted | `services/**` | None |

## Statuses

`Proposed` → `Accepted` → (`Superseded` | `Deprecated`)

Superseded ADRs stay in the repo. History is never deleted.

See [ADR-TEMPLATE.md](ADR-TEMPLATE.md) to add a new decision.
