# Contributing

This repository is a product architecture specification. Contributions must keep the document set internally consistent.

## Glossary lock

Every term used in a document must match [glossary.md](glossary.md). The locked names are:

Agent, Channel, Operator, Agent computer, Operator computer, Wake, Routine, Skill, Connector, Worker, Desktop, Store, Turn, Memory, Project, Plugin.

Do not substitute "bot", "user" (for the human), "VM", "cron job" (for Routine), or "integration" (for Connector) as if they were the same objects.

## Examples

Use only the fictional Agents:

- Atlas — `00000000-0000-4000-8000-000000000001` — operator-facing pane
- Nia — `00000000-0000-4000-8000-000000000002` — research specialist
- Vega — `00000000-0000-4000-8000-000000000003` — implementation specialist

Call the human **the operator**. Never a real first name.

Paths: `<store>/`, `<agent-computer>/`, `<operator-computer>/`. Never a real absolute path.

## UI

Do not invent product UI paths. Document only the verified facts in [docs/12-application-ui.md](docs/12-application-ui.md). If unknown, write `Not observed / not specified`.

## Skills

Catalog Skills from the sanitized product list. Include a body only for generic product Skills that do not name people. A user-authored routing Skill is a **pattern** only: one pane, one owner, no fan-out. Do not copy a live roster.

## Safety

Do not document safety-classifier internals, exploits, or credential theft. Auth handoff (the operator signs in on the Agent Desktop; the Agent never sees the password) is allowed and is the correct pattern.

## Invariants

New rules go in [boundaries/invariants.md](boundaries/invariants.md) as testable statements: Given A, when B, then C.

## Links

Cross-link with relative markdown links. A new document must be added to the tree map in [README.md](README.md).

## License

Contributions are under the [MIT License](LICENSE).
