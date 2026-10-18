# ADR-003: Event-Driven Document Processing

Status: Accepted
Date: 2026-10-18
Owner: <dev name>
Related work: ARCH-155

## Context
Document processing is slow and bursty. Synchronous request/response processing ties up callers and fails badly under load.

Option A: Synchronous API call per document
- Simple to reason about
- Callers block; load spikes cause timeouts

Option B: Queue/event-driven processing
- Decouples upload from processing, absorbs bursts
- Needs retry, idempotency, and status tracking

## Decision
Use Option B. Uploads publish an event; workers consume and process asynchronously.

## Consequences
- Handlers must be idempotent.
- Callers poll or subscribe for status instead of waiting on a response.
- Operate and monitor the queue and dead-letter handling.

## Reconsider When
- Processing becomes consistently fast enough for synchronous use.
- Queue operating overhead outweighs its benefits.

## Applies To
- services/**

## Supersedes
None
