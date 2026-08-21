# Skills

[Skill](../glossary.md) catalog and bodies for the product. Source of truth for this tree is the sanitized product list, not a live workflow folder.

An Agent must read a Skill before following it. Wake injection is name + description only.

## Files

- [catalog.md](catalog.md) — every Skill: id/slug, source, one-line when-to-use.
- `<slug>.md` — frontmatter plus body.

## Sources

| Source | Meaning |
| --- | --- |
| managed | Cursor-managed, read-only product Skills. |
| plugin | Installed with a Plugin, read-only. |
| user | Operator-created. |

## Body policy

- Generic product Skills may include a body.
- The user-authored routing Skill is a **pattern** only: one pane, one owner, no fan-out. No live roster. See [operator-routing-pane.md](operator-routing-pane.md).
- Plugin-internal eval / benchmark / release Skills are omitted unless labeled internals. They are not in this catalog.

## Follow

See [docs/09-skills.md](../docs/09-skills.md) and [examples/09-skill-follow.md](../examples/09-skill-follow.md).
