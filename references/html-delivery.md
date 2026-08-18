# HTML delivery

## Contents

1. Output contract
2. Report structure
3. Diagram styling
4. Validation
5. Handoff

## Output contract

- Create one standalone `.html` file in a durable, user-accessible directory.
- Keep an editable source fragment when the visualization system requires it.
- Return a clickable absolute file path in the final response.
- Do not return only an inline preview when the user asks for a file.
- Avoid remote data calls and keep the document readable without network access.

## Report structure

- Lead with the outcome and evidence legend.
- Add a compact table of contents.
- Use semantic headings, tables, lists, details, and accessible diagram labels.
- Put wide tables inside horizontal overflow containers on narrow screens.
- Keep evidence IDs visible near claims and nodes.
- Separate Confirmed, Reasonable inference, Recommended design, and Unknown through labels and line style, not color alone.

## Diagram styling

- Arrange layers top to bottom.
- Group same-layer components in a labeled subgraph or section.
- Label flows: call, read, write, event, confirmation, asset reference, state update.
- Use solid borders/lines for confirmed items.
- Use dashed borders/lines for inferred items.
- Use dotted or distinctly labeled borders/lines for recommended items.
- Use warning styling for unknown responsibility and problem styling for current conflicts.
- Include a legend and a short critical path.

For Mermaid requirements, include valid Mermaid source even when also rendering a static HTML/SVG fallback. Use `stateDiagram-v2` for a single Agent, `erDiagram` for entities, and `sequenceDiagram` for user-to-Agent-to-tool-to-model-to-asset flow.

## Validation

Before handoff:

1. Parse HTML and confirm tags close.
2. Check the source stays below the visualization size limit.
3. Verify no literal escaped markup such as `\"` or fake `\n` appears.
4. Render near 1024 px, 736 px, and 360 px widths.
5. Check table overflow, heading wrapping, diagram labels, legends, themes, and expand behavior.
6. Verify the standalone export exists and has nonzero size.
7. Confirm all requested sections appear in the requested order.

## Handoff

Return a concise completion statement and the clickable standalone HTML path. Add an inline preview reference only when the host visualization system requires it. Do not make the user ask a second time for the file.
