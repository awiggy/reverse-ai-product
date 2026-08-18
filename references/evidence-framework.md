# Evidence framework

## Contents

1. Evidence levels
2. Source catalog
3. Conflict rules
4. Safety checklist

## Evidence levels

Use exactly four levels:

- **Confirmed**: visible page text, button, form, Agent label, asset, tool result, state change, error, official documentation, or reproducible result directly supports the claim.
- **Reasonable inference**: multiple confirmed facts require or strongly suggest the behavior, but the implementation is not visible.
- **Recommended design**: proposed architecture or guardrail that improves correctness, stability, safety, cost, or user experience.
- **Unknown**: current evidence is insufficient or contradictory.

Never collapse inference into fact because it is conventional or technically necessary.

## Source catalog

Create one row per independently reviewable fact:

| Field | Meaning |
|---|---|
| evidence_id | Stable ID such as S01 or E-UI-03 |
| source_type | screenshot, browser, chat export, official page, recording |
| chronological_position | Earliest-to-latest order or explicit unknown |
| visible_agent | Exact visible name or unknown |
| page_region | chat, canvas, toolbar, form, task panel, asset library, preview |
| exact_text | Short verified UI quote; avoid long copyrighted copying |
| visible_action | User click/input or system result |
| visible_asset | Script, image, video, audio, prompt, version, or none |
| visible_state | waiting, generating, completed claim, error, etc. |
| conflict_with | Other evidence ID when states disagree |
| supports | Claim or architecture component supported |
| level | Confirmed, inference, recommended, unknown |
| limitation | What this evidence cannot prove |

## Conflict rules

Compare five state projections:

| Projection | Typical evidence |
|---|---|
| Chat | Agent says planning, generating, completed, failed |
| Task | active task, progress, idle, retrying |
| Canvas | nodes, cards, thumbnails, dependencies, edit/delete icons |
| Asset history | stored assets, versions, empty state, rollback |
| Preview/export | playable media, completeness warning, editor/download entry |

If they disagree:

1. Record each visible state as confirmed.
2. Record the inconsistency as confirmed.
3. Mark the backend cause unknown or inferred.
4. Do not select the most convenient state as the truth.
5. Recommend a versioned workflow truth source only in To-Be.

## Safety checklist

- Keep live inspection read-only.
- Do not trigger generation, regeneration, publishing, deletion, purchase, recharge, or overwrite.
- Do not reveal cookies, tokens, passwords, authorization headers, account identifiers, or sensitive identity data.
- Use official product sources only for external corroboration.
- Do not open hidden developer surfaces solely to infer proprietary architecture.
- Separate exact UI text from OCR uncertainty.
- Verify Agent completion against assets and state.
- Mark missing, clipped, or ambiguous evidence explicitly.
