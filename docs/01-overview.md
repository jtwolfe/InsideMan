# Overview

Grok Bot is a multi-agent runtime. The operator talks to one or more [Agents](02-identity.md). Each Agent is a durable person. The model that speaks for an Agent is stateless per [Wake](04-turns-and-runtime.md). Durable state lives in the [Store](13-store-layout.md).

See [glossary.md](../glossary.md) for locked names. See [README.md](../README.md) for the one-page story and the mermaid of Agents, two computers, and two buses.

## Core objects

| Object | Durable key | Notes |
| --- | --- | --- |
| Agent | UUID | Display name is not the key. Folder `<store>/agents/<uuid>/`. |
| Channel | Name + member UUID list | Cap 6. Does not nest. On-disk group marker was not observed in Agent folders. |
| Project | Slug | `<store>/projects/<slug>/`. An Agent lists slugs in `projects.json`. |
| Routine | Slug under the Agent | Cron **or** listeners, never both. |
| Skill | Frontmatter `name` | Global reusable template. Read before follow. |
| Connector | Stable server id | MCP. Discover, then call. |
| Worker | Dispatch id | No user-visible voice. |

## Two computers

- [Agent computer](05-shared-computer-and-desktop.md): one Linux machine shared by all of the operator's Agents.
- [Operator computer](06-operator-computer.md): the human's machine, reached through an approval-gated bridge.

A path on one is not visible on the other. Copy is an explicit transfer.

## Two buses

- [Operator bus](03-messaging.md): Operator ↔ Agent. Only user-visible voice. Explicit send.
- [Agent bus](03-messaging.md): Agent ↔ Agent or Channel. Async. Later Wake.

Fan-out (many Agents or a group) is a real side effect in the operator's chats. Default is one owner, not a blast.

## Wake contract

Each Wake injects:

1. Profile (`name`, `description`, `title`, `avatarShape`, `avatarColor`)
2. Memory (tiered; most-specific wins)
3. Teammate roster (name + UUID + one-line brief)
4. Tools
5. Skills catalog

The hard part of a rebuild is the Wake router: durable people, stateless turns.

## Hosted runtime (generic)

Desktop start/stop scripts, a [window router](05-shared-computer-and-desktop.md), store-sync / transcript-mirror workers, a Chromium profile on the Agent computer, and a health check (machine-id, Chrome, DNS, clock, D-Bus). Runtime may be local Docker or a brokered pod.

Recovery is only the two paths in Settings → Updates. See [docs/12-application-ui.md](12-application-ui.md).

## Fictional examples

This specification uses only:

- Atlas `00000000-0000-4000-8000-000000000001` — operator-facing pane
- Nia `00000000-0000-4000-8000-000000000002` — research specialist
- Vega `00000000-0000-4000-8000-000000000003` — implementation specialist

Worked sequences: [examples/](../examples/01-operator-message-turn.md).

## Boundaries

Testable rules: [boundaries/invariants.md](../boundaries/invariants.md).
Tool surfaces: [boundaries/interfaces.md](../boundaries/interfaces.md).
