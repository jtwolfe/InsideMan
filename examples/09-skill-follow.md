# Example: Skill follow

Atlas connects a Connector. Atlas must read `add-connector` in the current Turn before following it.

## Actors

- Operator
- Atlas `00000000-0000-4000-8000-000000000001`

## Frontmatter (catalog entry)

```yaml
---
name: add-connector
description: Walk through connecting a new MCP connector. Search the catalog, install, and authenticate.
---
```

## Sequence

1. Operator: "Connect Slack."
2. Atlas wakes. The skills catalog lists `add-connector` by name + description.
3. Atlas reads the Skill body. Following without a read is invalid.
4. Atlas follows [skills/add-connector.md](../skills/add-connector.md): identify Slack, search, confirm with a question widget, stop the Turn.
5. On the next Turn, after the operator answers Yes, Atlas installs.
6. If status is `needsAuth`, the host authors a connect card. Atlas does not paste a link.
7. New Slack tools are available on the message after install, not the install Turn.
8. Atlas sends a short confirmation and one concrete next action.

## Invariants exercised

I31, I33, I34.

## Related

- [docs/09-skills.md](../docs/09-skills.md)
- [docs/10-connectors.md](../docs/10-connectors.md)
