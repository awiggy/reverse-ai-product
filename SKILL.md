---
name: reverse-ai-product
description: Evidence-led reverse analysis of AI creative products from screenshots, screen recordings, browser-visible chats, canvases, forms, assets, task states, model selectors, billing displays, and errors. Use when Codex must reconstruct a product's user journey, identify observable Agents, write Agent I/O or tool contracts, map global context and asset dependencies, derive a functionally equivalent single-Agent System Prompt without claiming official wording, produce As-Is/To-Be product architecture, or deliver the result as a traceable HTML visualization.
---

# Reverse AI Product

Reconstruct what users and the interface demonstrably do, then separate the current architecture from behavior-based inference and recommended design. Keep every major conclusion traceable to visible evidence.

## Load references selectively

- Read [references/evidence-framework.md](references/evidence-framework.md) before collecting or classifying evidence.
- Read [references/deliverable-schemas.md](references/deliverable-schemas.md) for user journeys, Agent contracts, System Prompts, architecture reports, ER diagrams, sequence diagrams, and tests.
- Read [references/architecture-patterns.md](references/architecture-patterns.md) when deriving global context, state, asset, model, billing, safety, or infrastructure architecture.
- Read [references/html-delivery.md](references/html-delivery.md) only when the user requests HTML, a diagram, or a packaged visual report.

## Choose the requested depth

Do not automatically perform every level. Follow the user's requested scope.

1. **Journey only**: reconstruct the chronological user experience, decisions, corrections, failures, and asset changes.
2. **Agent contracts**: identify only Agents supported by evidence; map inputs, observable judgments, tools, outputs, context reads/writes, and handoffs.
3. **Single-Agent Prompt**: analyze one named Agent and derive a functionally equivalent Prompt with evidence labels and tests.
4. **Full architecture**: combine journeys, Agent contracts, tools, context, assets, models, state, billing, safety, knowledge, infrastructure, risks, and As-Is/To-Be.
5. **HTML delivery**: render the requested report or architecture as a standalone file and return its clickable absolute path.

Stop at the requested level. Do not continue into hidden prompts, internal tools, or other Agents after the user says to stop or wait for confirmation.

## Apply hard evidence boundaries

- Treat a visible Agent statement such as “completed” as a claim, not proof.
- Confirm actions only through a visible result card, state change, asset change, tool result, or reproducible page result.
- Treat “thinking complete” and “planning complete” only as public summaries. Never claim access to hidden chain-of-thought.
- Never invent official function names, API parameters, database tables, queues, cloud vendors, model suppliers, or System Prompt wording.
- Use functional tool names such as `<generate-video>` and label them “non-official functional name” unless the exact UI name is visible.
- Do not use screenshot filenames, folder names, OCR guesses, or Agent promises as stronger evidence than the actual page.
- Record conflicts instead of choosing one side. Examples: chat says generating while task panel says idle; canvas has assets while asset library is empty.
- Label every conclusion as **Confirmed**, **Reasonable inference**, **Recommended design**, or **Unknown**.
- Protect credentials and sensitive data. Never inspect or output cookies, tokens, passwords, authorization headers, or personal identity data.
- Keep browser inspection read-only unless the user explicitly authorizes an in-scope mutation. Never trigger generation, regeneration, deletion, purchase, recharge, publication, or overwrite during evidence collection.
- Use only official product pages or official documentation for external corroboration. Do not treat third-party speculation as current architecture evidence.

## Execute the evidence workflow

### 1. Inventory the source set

Enumerate all screenshots, recordings, exported chats, HTML files, or browser states. Record source ID, filename, dimensions, apparent stage, and accessibility.

For screenshots:

- Sort by visible chronology, not filename alone.
- Inspect the full image and relevant crops.
- Use OCR only as an index or transcription aid; visually verify all important text.
- Capture buttons, forms, cards, canvas nodes, status panels, balances, errors, previews, editing entries, and asset history.

For live browser evidence:

- Use a browser-control skill when available and read its full instructions first.
- Reuse the existing signed-in session only for visible, read-only inspection.
- Do not open developer tools to extract secrets or hidden network credentials.

### 2. Build the evidence catalog

Assign stable evidence IDs such as `S01`, `S02`, or `E-CHAT-01`. Quote short UI text exactly and record the visible Agent, component, asset, state, and conflict.

Use the catalog schema in `references/evidence-framework.md`.

### 3. Reconstruct chronology

Start at the earliest visible user input. For every step record:

- user goal and action;
- active or visible Agent;
- page feedback;
- decision required;
- tool or result evidence;
- global-context change;
- asset creation or modification;
- next handoff;
- correction, failure, interruption, or unknown branch.

Do not fill unseen gaps with a smooth narrative. Insert an explicit evidence gap.

### 4. Reconcile five state projections

Compare at least:

1. chat claims;
2. task or progress panel;
3. canvas nodes and assets;
4. asset library or history;
5. preview/export readiness.

Create a conflict entry whenever these disagree. Treat the conflict itself as a confirmed product fact and its backend cause as inference or unknown.

## Build Agent contracts

Identify Agents in chronological order. Record an Agent only when its name, role label, reply ownership, invitation, or unambiguous functional stage is visible.

For each Agent inspect six input sources:

1. user current input;
2. user long-term information;
3. project global context;
4. upstream Agent output;
5. platform public assets or rules;
6. tool and runtime results.

Then record:

- core goal and boundary;
- trigger, predecessor, successor, and possible re-entry;
- observable functional judgments, never hidden reasoning;
- functional tools and execution evidence;
- user reply, UI components, structured fields, assets, status, and downstream tasks;
- context reads/writes, producer, consumer, update time, and evidence level;
- completion gate, exceptions, retry, interruption, and unknowns.

If a stage clearly exists but its Agent name is clipped, use “role-stage Agent” and mark the precise name unknown. Do not promote a familiar industry role to fact.

## Derive a single-Agent functional Prompt

Do this only for the Agent named by the user.

1. Collect every appearance of that Agent.
2. Establish its boundary, trigger, stop conditions, auto-continue conditions, confirmation gates, re-entry, and handoff.
3. Define input, output, tool, context, and state-machine contracts.
4. Convert evidence into four rule classes: fact rule, inference rule, recommended rule, unknown.
5. Write a usable Prompt with role, goal, boundaries, inputs, context protocol, workflow, tools, confirmation, validation, modification, exceptions, state machine, handoff, completion, and output schema.
6. Mark semantic placeholder fields and non-official tool names explicitly.
7. Require result validation; never let the Prompt complete on its own natural-language claim.
8. Add a rule-to-evidence trace table and at least six tests: normal, missing input, local modification, tool failure, interruption, and state conflict.

Do not claim the result is the product's official Prompt.

## Derive full product architecture

Separate three views:

- **As-Is confirmed**: directly visible components, flows, models, assets, decisions, and errors.
- **As-Is inferred**: capabilities required to explain observed behavior, such as project context, asynchronous tasks, asset persistence, or routing.
- **To-Be recommended**: stability mechanisms such as a single state source, asset versions, dependency invalidation, idempotent retries, billing reservation, completion validation, tracing, and tenant isolation.

Cover these layers when requested:

1. user and channels;
2. interaction and workspace;
3. product applications;
4. Agent and workflow orchestration;
5. tools and services;
6. model access and routing;
7. global context and data;
8. knowledge and public/private assets;
9. infrastructure and governance.

Do not name a database, queue, cloud, CDN, programming language, or vendor as confirmed unless official evidence directly supports it. Describe required capability, possible class of technology, recommended design, and why the actual implementation is unknown.

## Model context as structured slices

Avoid one undifferentiated “global context” box. Evaluate slices such as:

- UserContext;
- ProjectConfig;
- ScriptContext;
- CharacterContext;
- SceneContext;
- PropContext;
- StoryboardContext;
- AssetContext;
- WorkflowState;
- BillingContext;
- EvaluationContext.

Treat these names as analysis templates. Mark actual visible fields separately from inferred objects and recommended fields.

For every asset-bearing context, look for stable IDs, versions, producer runs, parent references, visibility, confirmation, and downstream consumers. If absent, mark unknown and recommend an immutable version plus dependency graph rather than silently assuming one exists.

## Validate completion and failure behavior

Check whether completion requires all of the following:

- required output assets exist;
- global context is updated;
- page, task, canvas, asset, and preview states agree;
- the current revision is confirmed;
- downstream handoff data is complete;
- relevant quality checks pass;
- billing and safety states are settled;
- no active interruption or blocking error remains.

Check failure branches for input gaps, dependency failures, model failure, safety block, insufficient balance, state-write failure, duplicate request, interruption, downstream startup failure, and partial final media.

When evidence is missing, record the branch as unknown. When recommending behavior, require idempotency and avoid repeated charges or duplicate assets.

## Produce traceable deliverables

Use the exact table and diagram schemas in `references/deliverable-schemas.md`. Include evidence IDs inside journey nodes, Agent cards, architecture components, and key rules.

For diagrams:

- use solid lines for confirmed flows;
- use dashed lines for reasonable inference;
- use dotted or distinct recommended styling for suggested design;
- label edges with actions such as call, read, write, event, confirmation, asset reference, and state update;
- include a visible legend;
- show failure and correction branches, not only the happy path.

## Deliver HTML correctly

When HTML is requested, read `references/html-delivery.md` and use the available visualization capability if appropriate. Keep an editable fragment as the source, export a standalone `.html` file to a durable user-accessible location, test desktop and narrow layouts, and return a clickable absolute file path.

Do not answer with only an inline preview when the user asks for an HTML file.
