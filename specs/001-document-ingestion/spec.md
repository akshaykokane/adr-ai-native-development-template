# Spec 001: Document Ingestion Pipeline

> Example spec showing how a spec consumes ADRs and promotes new decisions.

Status: Approved
Related work: FEAT-210

## What and why
Users upload PDFs. The system extracts text and makes it searchable within 5 minutes of upload.

Acceptance criteria:
- Upload returns immediately with a document ID.
- Status is queryable: `queued | processing | done | failed`.
- Failed documents are retried up to 3 times.

## Applicable decisions (read before planning)

| ADR | Constraint it imposes on this feature |
|---|---|
| [ADR-001](../../docs/decisions/ADR-001-cpu-processing.md) | Text extraction runs on CPU. No GPU libraries or instances. |
| [ADR-002](../../docs/decisions/ADR-002-storage-strategy.md) | PDF bytes go to object storage; only metadata and blob reference go to the database. |
| [ADR-003](../../docs/decisions/ADR-003-event-driven-processing.md) | Upload publishes an event; processing is asynchronous and idempotent. |

## Conflicts with accepted ADRs
None. The 5-minute target is within the CPU latency we accepted in ADR-001. If measured latency breaks it, that triggers ADR-001's "Reconsider When" and needs a new ADR, not a quiet switch to GPU.

## Plan (how)
1. Upload API writes the PDF to object storage, inserts a metadata row, publishes `document.uploaded`.
2. A CPU worker consumes the event, extracts text, writes results, updates status.
3. Retries use exponential backoff; a dead-letter queue catches the third failure.
4. Search index is updated from the worker output.

## ADR candidates
- [x] Use an OCR fallback only for scanned PDFs → ADR-009 (Proposed)
- [ ] Retry policy (3 attempts, exponential backoff): implementation detail, no ADR.

## Tasks
- [ ] Upload endpoint and storage write
- [ ] `document.uploaded` event and worker
- [ ] Status endpoint
- [ ] Retry and dead-letter handling
- [ ] Search index update

## Change log

| Date | Change | Why | PR / commit | ADR |
|---|---|---|---|---|
| 2026-10-18 | Initial approved spec | n/a | n/a | ADR-001, 002, 003 |
| 2026-10-25 | Retries reduced from 5 to 3 | Retries beyond 3 never succeeded in testing | #131 | none (implementation detail) |
