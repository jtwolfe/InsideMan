# Interfaces

Tool surfaces. Interfaces, not live IDs. Names match [glossary.md](../glossary.md).

## User voice

The Operator bus. Delivery is an explicit send.

| Surface | Purpose |
| --- | --- |
| send text | Visible reply or result. |
| attachments | Files on the Operator bus. |
| question widgets | Operator choice. Ends the Turn; wait for the answer. |
| secret-request | Collect a secret via a card. Not for Plugin setup fields. |
| Cloud coding agent cards | Present remote branch / pull-request work. |
| emoji reaction | React to an operator message. |

Plain model text is not delivered.

## State

| Surface | Purpose |
| --- | --- |
| memory | Read / write Memory tiers. |
| routine | Create / update / expire Routines. |
| workflow | Enable Skills / workflows. |
| profile | Update `name`, `title`, `description`, `avatarShape`, `avatarColor`. |
| settings | Observed: `notifyOnAgentUpdates`. |
| avatar | Sibling image beside `profile.json`. |
| project join | List slugs in `projects.json`. |

## Agent computer

| Surface | Purpose |
| --- | --- |
| shell | Command execution on `<agent-computer>/`. |
| structured file read | Line-numbered / paged read. |
| screenshot | Read-only image of **this** Agent's Desktop. |

No click / type / scroll of the Agent's own Desktop.

## Operator computer

Approval-gated.

| Surface | Purpose |
| --- | --- |
| shell | Command on `<operator-computer>/` after approval. |
| read | Structured read after approval. |
| copy to Agent computer | Verbatim transfer. |
| copy from Agent computer | Verbatim transfer. |

## Web

| Surface | Purpose |
| --- | --- |
| search | Query the public web. |
| fetch | Read a URL as text. |

Fallback when no Connector exists. If a Connector exists, use it.

## MCP

| Surface | Purpose |
| --- | --- |
| discover | Schema and status. |
| call | Invoke a tool on a Connector. |

Auth via connect card. See [docs/10-connectors.md](../docs/10-connectors.md).

## Team

| Surface | Purpose |
| --- | --- |
| create / update Agent | Allocate UUID, folder, profile. |
| create / update Channel | Name + member UUID list (cap 6). |
| send to Agent | Agent-bus 1:1. May include images; may interrupt. |
| send to Channel | Text-only. Wakes every member. |

## Workers

| Surface | Purpose |
| --- | --- |
| task dispatch | Start a Worker. |
| check / message / stop | Inspect or halt a Worker. |
| Cloud coding agent launch | Remote branch + pull request. |
| Cloud coding agent reply | Follow-up to a remote run. |

## Plugins

| Surface | Purpose |
| --- | --- |
| search | Marketplace search. |
| install | Add a Plugin / Connector. |
| auth | Authenticate a Connector. |

## Window router

Not a speaking-Agent tool. Host table: Agent UUID → integer window id + opaque tokens. Describe the table, not live values.

## Out of scope

Safety-classifier internals, exploits, and credential theft are not interfaces in this specification.
