# Glossary

Canonical names. Use these spellings and capitalizations in every document. Do not introduce synonyms for the same object.

| Term | Meaning |
| --- | --- |
| Agent | Durable person. Canonical identity is a UUID. Display name is not the key. Folder: `<store>/agents/<uuid>/`. |
| Channel | Named group chat of Agent UUIDs (cap 6). Membership lets an Agent post. Channels do not nest. |
| Operator | The human. Never addressed by a first name in this specification. |
| Agent computer | One Linux machine shared by all of the operator's Agents. Same filesystem, installed tools, browser logins. Persistent across turns. |
| Operator computer | The human's machine. Approval-gated bridge. File copy both ways. A path on one computer is not visible on the other. |
| Desktop | Per-Agent private screen on the shared Agent computer. About 1280x800. An Agent cannot see another Agent's Desktop. |
| Wake | One model invocation. The model is stateless per turn. The host injects profile, memory, teammate roster, tools, and the skills catalog. |
| Turn | The span of one Wake, including tool calls, until the model stops. |
| Store | Durable on-disk state for Agents, Projects, Memory, Routines, and related objects. Root written as `<store>/`. |
| Memory | Durable notes the host injects on Wake. Tiers: Agent memory > Project memory > shared user memory. Most-specific wins. |
| Project | Named work context under `<store>/projects/<slug>/`. An Agent may join via `projects.json`. |
| Routine | Standing order. Cron in the operator's local timezone, **or** event listeners. Never both on one Routine. |
| Skill | Reusable `SKILL.md` template (YAML frontmatter `name` + `description` + body). Sources: user-created, Cursor-managed (read-only), plugin-installed (read-only). |
| Connector | MCP path to an external service. Discover schema, then call. Preferred over the browser when a Connector exists. |
| Worker | Background actor without user voice: executor, browserUse, computerUse, watchVideo / videoReview, Cloud coding agent. |
| Plugin | Marketplace bundle of Connectors and Skills (or a curated Connector). Plumbing; say "Connector" to the operator. |
| Operator bus | Operator ↔ Agent messaging. The Agent's only user-visible voice. Delivery is an explicit send. |
| Agent bus | Agent ↔ Agent or Channel messaging. Async, fire-and-forget. Delivery wakes the target on a later turn. |
| Window router | Host table mapping Agent UUID to an integer window id plus opaque tokens. Describe the table, not live values. |
| Cloud coding agent | Remote Worker that edits a repository on a branch and opens a pull request. Not a clone onto either computer by default. |

## Fictional example Agents

These three identities are the only Agents named in examples.

| Display name | UUID | One-line brief |
| --- | --- | --- |
| Atlas | `00000000-0000-4000-8000-000000000001` | Operator-facing pane |
| Nia | `00000000-0000-4000-8000-000000000002` | Research specialist |
| Vega | `00000000-0000-4000-8000-000000000003` | Implementation specialist |

## Path placeholders

| Placeholder | Meaning |
| --- | --- |
| `<store>/` | Durable product state root. |
| `<agent-computer>/` | Filesystem of the shared Agent computer. |
| `<operator-computer>/` | Filesystem of the operator's machine. |
| `<slug>` | Project or Routine slug. Fictional in examples. |
| `<uuid>` | Agent UUID. |
| `<operator-local>` | The operator's local timezone. Never a named real timezone. |

## Related

- Product model: [docs/01-overview.md](docs/01-overview.md)
- Identity: [docs/02-identity.md](docs/02-identity.md)
- Store layout: [docs/13-store-layout.md](docs/13-store-layout.md)
