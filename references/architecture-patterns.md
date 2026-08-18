# Architecture patterns

## Contents

1. Structured context
2. Asset dependencies
3. Workflow truth source
4. Model, billing, and safety
5. Knowledge architecture
6. Risk checklist

## Structured context

Use these as analysis templates, not assumed product field names:

| Slice | Typical contents |
|---|---|
| UserContext | locale, membership, balance, private assets, preferences, permissions |
| ProjectConfig | format, duration, ratio, language, style reference, model settings |
| ScriptContext | original input, structured script, version, confirmation |
| CharacterContext | stable character ID, prompt, references, Face ID, voice, version |
| SceneContext | scene ID, description, main image, multiview assets, version |
| PropContext | prop ID, description, image, scene/shot references, version |
| StoryboardContext | shot ID, order, duration, entity references, prompts |
| AssetContext | asset ID, type, immutable version, URI, producer, parents, visibility |
| WorkflowState | revision, active Agent, task, confirmation, error, interruption, completion |
| BillingContext | estimate, reservation, charge, refund, invocation reference |
| EvaluationContext | feedback, validator results, failure reason, accepted version |

For each slice distinguish visible values, inferred object boundaries, recommended fields, and unknowns.

## Asset dependencies

Recommend this when current evidence does not prove an equivalent mechanism:

1. Assign stable entity and asset IDs.
2. Keep generated media immutable; create a new AssetVersion for every change.
3. Store producer AgentRun, ToolCall, ModelInvocation, template version, model version, and parent references.
4. Represent dependency edges explicitly from script through entities and shots to media and final composition.
5. On upstream modification, mark only dependent outputs stale.
6. Preserve accepted and previous versions for comparison and rollback.
7. Do not delete or overwrite confirmed history during recomputation.

## Workflow truth source

Treat chat, task panel, canvas, asset history, and preview as projections of one versioned workflow state. Recommended states:

- waiting_input
- planning
- waiting_confirmation
- executing
- validating
- retrying
- failed_state_sync
- failed
- interrupted
- handoff
- completed

Complete only if the required asset exists, context write succeeded, the current revision passed validation, confirmation is recorded, and downstream handoff is complete.

Use event IDs and expected revisions for state-changing commands. Use idempotency keys for chargeable or asset-producing operations. When a tool succeeds but state persistence fails, query the existing result and repair state instead of repeating the business call.

## Model, billing, and safety

Do not infer dynamic multi-model routing from one visible selector. A recommended model gateway should include:

- capability registry for modality, duration, resolution, reference support, language, safety, cost, latency, and failure rate;
- parameter validation before invocation;
- explicit consent for model, quality, or resolution downgrade;
- immutable ModelInvocation records;
- retry policy and fallback versioning;
- pre- and post-generation safety results.

Enforce safety and billing in platform services, not only Agent Prompts.

Recommended billing lifecycle:

`estimate → user confirmation → reserve → invoke → settle on success OR release/refund on failure/cancel`

Bind every ledger record to the invocation and idempotency key.

## Knowledge architecture

Separate project data, user private assets, platform public assets, professional knowledge, style packages, prompt templates, model capability knowledge, safety/copyright/billing rules, and feedback/model-performance data.

Version public knowledge and style packages. Keep private assets in tenant-scoped namespaces with explicit reuse permission. Do not turn project feedback into cross-user training data without authorization and de-identification.

## Risk checklist

- chat/task/canvas/asset/preview state conflict;
- Agent claims complete before tool or asset completion;
- asset succeeds but context write fails;
- upstream edit does not invalidate dependent output;
- retry duplicates assets or charges;
- duration deviates from project intent;
- style, character, dialogue, or audio/video synchronization lacks validation;
- safety errors are mischaracterized;
- interruption does not stop workers;
- private assets leak across users or tenants;
- knowledge or model capability rules become stale;
- final preview opens before required media is ready.
