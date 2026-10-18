# ADR-008: Adopt GPU-Based Processing

> Example only. Shows how a superseding ADR looks. Not part of the active decision set.

Status: Accepted
Date: <date>
Supersedes: ADR-001

## Context
GPU infrastructure costs have decreased. Updated benchmarks indicate that GPU processing now meets our operating budget.

## Decision
Move document processing to GPU infrastructure.

## Consequences
- Reduced processing latency.
- New infrastructure and monitoring requirements.
- Migration and rollback plan required.

## When this happens
1. Update ADR-001: set `Status: Superseded by ADR-008`.
2. Update `docs/decisions/INDEX.md` (ADR-001 → Superseded, add ADR-008).
3. Update `.github/instructions/architecture.instructions.md` to match.
