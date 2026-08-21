# Skills

A [Skill](../glossary.md) is a reusable `SKILL.md` template. YAML frontmatter `name` + `description` + body.

An Agent must read a Skill before following it. The catalog injected on Wake is name + description only.

## Sources

| Source | Mutability | Notes |
| --- | --- | --- |
| user-created | Writable by the operator | Private skills appear under Plugins → Your plugins. |
| Cursor-managed | Read-only | Product Skills. |
| plugin-installed | Read-only | Shipped inside a [Plugin](10-connectors.md). |

## Frontmatter example (fictional / product)

```yaml
---
name: add-connector
description: Walk through connecting a new MCP connector. Search the catalog, install, and authenticate.
---
```

## Follow rule

Given Atlas decides to connect Slack, when the catalog lists `add-connector`, then Atlas reads `add-connector` in the current Turn before following its steps.

Worked sequence: [examples/09-skill-follow.md](../examples/09-skill-follow.md).

## Routines

A [Routine](08-routines.md) may point at a Skill. The Wake still requires a read before follow.

## User-authored routing Skill

A user-authored routing Skill is documented as a **pattern** only. See [skills/operator-routing-pane.md](../skills/operator-routing-pane.md).

Pattern:

- The operator talks to one pane Agent.
- The pane routes to exactly one owner.
- The owner files a short report (`result` / `decision` / `blocker`).
- No fan-out.

Do not document a live roster. Examples in this repository use only Atlas (pane), Nia (research), Vega (implementation).

## Catalog

The product catalog: [skills/catalog.md](../skills/catalog.md). Bodies: [skills/](../skills/README.md).

## enabled-workflows.json

Optional file on the Agent folder. Not observed / not specified: the exact JSON schema. Treat it as an enablement list, not a Skill body store.
