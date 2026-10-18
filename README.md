# ADR-Driven AI-Native Engineering Template

Companion repo for *Teaching AI Agents to Remember: ADRs, GitHub, and Engineering Decisions* (Part 2/5 of the AI-Native Software Engineering series).

It shows how to make architectural decisions discoverable by developers, coding agents, and reviewing agents.

```
.
├── AGENTS.md                              # standing guidance for coding agents
├── docs/
│   ├── decisions/
│   │   ├── INDEX.md                       # catalog agents read first
│   │   ├── ADR-TEMPLATE.md
│   │   ├── ADR-001-cpu-processing.md
│   │   ├── ADR-002-storage-strategy.md
│   │   └── ADR-003-event-driven-processing.md
│   └── examples/
│       └── ADR-008-superseding-example.md # how to supersede a decision
└── .github/
    ├── copilot-instructions.md            # repo-wide Copilot context + review rules
    ├── pull_request_template.md           # ADR impact fields
    └── instructions/
        └── architecture.instructions.md   # path-specific instructions
```

## How to use this template
1. Copy these files into your repository.
2. Replace the sample ADRs with your real decisions; keep IDs stable.
3. Keep `Applies To` in each ADR, `INDEX.md`, and `applyTo` in instruction files in sync.
4. Verify which instruction files your coding and reviewing agents actually consume. Support varies by tool.

## Important limitation
Instructions are not enforcement. For high-impact decisions, back the ADR with automated checks (dependency rules, cost policies, architecture tests, required approvals on protected paths). The ADR says *why*; the check verifies *whether*.
