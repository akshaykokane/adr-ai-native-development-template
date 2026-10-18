# ADR-002: Object Storage for Raw Documents, Relational DB for Metadata

Status: Accepted
Date: 2026-10-18
Owner: <dev name>
Related work: ARCH-150

## Context
Documents are large, immutable blobs. Metadata (owner, status, timestamps) is small, relational, and queried often.

Option A: Store everything in the relational database
- Simple, single system
- Large blobs inflate database size, backups, and cost

Option B: Object storage for blobs, relational DB for metadata
- Cheap, scalable blob storage
- Two systems to keep consistent

## Decision
Use Option B. Store raw documents in object storage; store only metadata and blob references in the relational database.

## Consequences
- Never store document bytes in the relational database.
- Writers must handle blob/metadata consistency (write blob first, then metadata).

## Reconsider When
- Document sizes drop to a point where blob storage adds no value.
- Consistency issues between the two stores become frequent.

## Applies To
- services/storage/**
- infrastructure/storage/**

## Supersedes
None
