# AGENTS.md

Standing guidance for AI coding agents working in this repository.

## Engineering Decision Guidance

Before planning or modifying code:

1. Identify the components and files affected.
2. Read `docs/decisions/INDEX.md`.
3. Open applicable accepted ADRs (match on the `Applies To` paths).
4. Identify architectural constraints and trade-offs.
5. Include relevant ADR IDs in the implementation plan.
6. Do not silently overturn an accepted decision.
7. If a decision appears outdated or conflicts with the task, flag it and propose reconsideration.
8. In the final summary, report ADRs consulted and any potential conflicts.

Treat ADRs as decision context, not as permanently unchangeable rules.

## Risk-Based Review

| Change type | What the agent does |
|---|---|
| Routine implementation within approved constraints | Identify relevant ADRs and proceed. |
| Material architectural change | Write a short plan, explain the trade-off, request developer review. Significant changes go to the team. |
| Conflict with an accepted ADR | Propose an ADR amendment or a new superseding ADR **before** changing the architecture. |

## Rules for Writing ADRs

- Use `docs/decisions/ADR-TEMPLATE.md`.
- Use the next free stable ID (`ADR-NNN`). Never reuse or renumber IDs.
- AI-drafted ADRs must be `Status: Proposed`. Only a human confirms `Accepted`.
- Never delete an ADR. Mark it `Superseded` and link to the replacement.
- Update `docs/decisions/INDEX.md` in the same PR.
- Do not duplicate decision content in this file or in Copilot instructions; link to the ADR.

## Evidence Requirement

Adding this file does not prove it was followed. Every PR must show which ADRs were consulted (see the PR template).
