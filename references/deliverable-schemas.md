# Deliverable schemas

## Contents

1. User journey
2. Agent inventory and contract
3. Single-Agent Prompt
4. Full architecture
5. Diagram rules

## User journey

Evidence table columns:

`Stage | User goal | User action | Page feedback | Decision | Page/asset change | Friction | Evidence`

Three swimlanes: User, Product interface, System result.

Include normal, correction, failure, insufficient-balance, and interruption paths. Use diamonds for decisions and label branches such as satisfied/not satisfied, success/failure, continue/interrupt, sufficient/insufficient balance.

## Agent inventory and contract

Inventory columns:

`Agent | First appearance | Trigger | Predecessor | Successor | Re-entry | Evidence level | Evidence`

Contract sections:

1. Core goal
2. Trigger conditions
3. Inputs by six source types
4. Observable judgments
5. Functional tools
6. User, UI, structured, asset, state, and downstream outputs
7. Global-context reads/writes
8. Completion conditions
9. Exceptions and retries
10. Unknown questions

Tool columns:

`Functional tool | Caller | Execution confirmation | Visible input/result | Boundary | Evidence`

Context columns:

`Field/object | Visible value/state | Producer | Consumer | Read/write judgment | Version/conflict | Evidence`

Producer-consumer columns:

`Data | Producer | Consumer | Use | Rerun after modification | Evidence`

## Single-Agent Prompt

Pre-Prompt order:

1. Evidence range and boundary
2. Input contract
3. Output contract
4. Tool contract
5. State machine and Mermaid source
6. Fact, inference, recommendation, and unknown rules

Prompt structure:

1. Agent name and role
2. Core objective
3. Task boundary
4. Input contract
5. Global-context protocol
6. Workflow with entry/exit conditions
7. Tool-call rules
8. User confirmation mechanism
9. Result validation
10. Modification and rollback
11. Exception handling
12. State machine
13. Downstream handoff
14. Completion conditions
15. Output schema

After the Prompt add:

- `Rule | Evidence | Classification | Replication purpose`
- At least six tests with `Input | Initial state | Expected judgment | Expected tools | Expected state | Forbidden behavior`

## Full architecture

Deliver in this order when requested:

1. One-sentence executive summary
2. Evidence sources and gaps
3. Core functional domains
4. End-to-end five-flow table
5. Nine-layer product architecture
6. Agent-tool-context relationships
7. Structured global context
8. Knowledge and public/private assets
9. Model access and routing
10. Technology capability/selection table
11. Entity table and Mermaid ER source
12. Mermaid sequence source
13. Product panorama architecture diagram
14. As-Is table
15. To-Be table
16. Prioritized risks
17. Component-evidence traceability
18. Unknown questions

End-to-end columns:

`Step | User flow | Agent control flow | Tool flow | Context/data flow | Asset flow | Confirmation/failure branch`

Technology columns:

`Capability domain | Required capability | Possible class | Recommended design | Why actual implementation is unknown | Level`

Entity columns:

`Entity template | Suggested fields | Relations | Page evidence | Classification`

As-Is columns: `Domain | Current behavior | Strength | Limitation | Evidence`

To-Be columns: `Recommended capability | Design | Write/validation point | User value | Priority`

Risk columns: `Priority | Risk | Trigger | Impact | Current evidence | Control`

Traceability columns: `Architecture component | Why needed | Page/official evidence | Classification | Confidence`

## Diagram rules

- Put same-layer components in one subgraph or visual group.
- Label every meaningful edge: call, read, write, event, confirmation, asset reference, state update.
- Use solid lines for confirmed, dashed for inferred, and dotted/distinct lines for recommended.
- Include a legend and current problems.
- Include data and status movement, not only component boxes.
- Ensure a product manager can trace demand entry, Agent selection, inputs, tools, assets, handoff, confirmation, failure, balance, knowledge, consistency, and completion.
