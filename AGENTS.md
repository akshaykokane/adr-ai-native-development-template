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

## Specs and ADRs

- Constitution (`.specify/memory/constitution.md`) = bylaws. Specs (`specs/NNN-feature/`) = work orders. ADRs (`docs/decisions/`) = case law.
- A spec says what we build and how, for one feature (forward-looking). An ADR says what we already decided and why (backward-looking, outlives the feature).
- Before writing a spec's plan: read `INDEX.md` and fill in the spec's "Applicable decisions" table.
- After writing the plan: list "ADR candidates", meaning only choices that meet the ADR threshold below. Most specs have zero or one. If unsure, do not write an ADR; note the choice in the spec's Plan or the PR and let a human decide.
- Choices below the threshold may live in the spec's Plan section.

## Keeping Specs Current

A spec describes the current intent, not the original plan. Code that changes behavior without updating its spec makes the spec a lie, and the next agent will trust it.

When a task or PR changes behavior covered by a spec in `specs/`:

1. Find the spec: check the task, branch name, or PR for a `specs/NNN-...` reference; otherwise search `specs/` for the affected feature.
2. Update the spec body (requirements, plan, tasks) so it describes the **new** truth. Do not leave the old value in place or only in a comment.
3. Append a row to the spec's **Change log**: date, what changed, why, PR/commit, ADR (if any).
4. Decide whether the change is a decision:
   - Pass the "could someone undo this without knowing why" test, or touches an accepted ADR's constraints? Write or supersede an ADR.
   - Otherwise (for example a box color changing red → blue), the spec change and change log entry are enough. No ADR.
5. If the change contradicts a spec's "Applicable decisions" table, treat it as an ADR conflict (see above).
6. Mark finished tasks done, and set `Status: Implemented` when all are complete.

If the requested change is not yet reflected in the spec, update the spec in the **same PR** as the code, not afterward.

## When an ADR Is Warranted

Write an ADR only for a big decision that meets at least one of these:

- Expensive to reverse (weeks of rework, a data migration).
- Crosses service or team boundaries, or changes a public contract.
- Sets a security, compliance, cost, or availability posture.
- Picks or replaces a core platform, framework, datastore, or hosting model.
- Overrides or supersedes an existing Accepted ADR.

Not ADRs: library choices, naming, refactors, bug fixes, UI tweaks, or anything reversible in a single PR. Record these in the spec, the PR description, or code comments.

## Risk-Based Review

| Change type | What the agent does |
|---|---|
| Routine implementation within approved constraints | Identify relevant ADRs and proceed. |
| Material architectural change | Write a short plan, explain the trade-off, request developer review. Significant changes go to the team. |
| Conflict with an accepted ADR | Propose an ADR amendment or a new superseding ADR **before** changing the architecture. |

## Rules for Writing ADRs

- Use `docs/decisions/ADR-TEMPLATE.md`. Keep it to one page; a few lines each for context, decision, and consequences.
- Draft at most one `Proposed` ADR per PR, and state which threshold criterion it meets (see "When an ADR Is Warranted"). Otherwise ask.
- `Proposed` ADRs not accepted within 30 days are closed as `Rejected` or folded into the spec.
- Use the next free stable ID (`ADR-NNN`). Never reuse or renumber IDs.
- AI-drafted ADRs must be `Status: Proposed`. Only a human confirms `Accepted`.
- Never delete an ADR. Mark it `Superseded` and link to the replacement.
- Update `docs/decisions/INDEX.md` in the same PR.
- Do not duplicate decision content in this file or in Copilot instructions; link to the ADR.

## Evidence Requirement

Adding this file does not prove it was followed. Every PR must show which ADRs were consulted (see the PR template).
