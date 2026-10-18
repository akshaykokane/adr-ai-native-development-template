# ADR-001: Use CPU-Based Processing

Status: Accepted
Date: 2026-10-18
Owner: <dev name>
Related work: ARCH-142

## Context
We evaluated two approaches for processing documents in the team's standup on 10 Oct 2026.

Option A: GPU-based processing
- Lower processing latency
- Requires dedicated GPU infrastructure
- Higher fixed operating cost

Option B: CPU-based processing
- Higher processing latency
- Uses existing infrastructure
- Lower and more predictable cost

Our current infrastructure budget does not support dedicated GPU capacity.

## Decision
Use Option B for document processing.

## Consequences
- Accept higher processing latency.
- Avoid dedicated GPU infrastructure costs.
- Monitor latency and processing costs.

## Reconsider When
- GPU infrastructure becomes affordable.
- Processing latency violates the approved SLA.
- Workload volume materially changes.

## Applies To
- services/document-processing/**
- infrastructure/document-processing/**

## Supersedes
None
