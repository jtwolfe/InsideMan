---
name: operator-routing-pane
description: A user-authored routing skill. Pattern: the operator talks to one pane agent; the pane routes to exactly one owner; the owner files a short report (result / decision / blocker); no fan-out.
---

# Operator routing pane (pattern only)

This is a user-authored routing Skill. Document the **pattern**, not a live roster.

## Pattern

1. The operator talks to **one pane Agent**.
2. The pane names **exactly one owner** for the job.
3. The pane hands the job to that owner only (Agent-bus 1:1).
4. The owner files a short report: `result` / `decision` / `blocker`, plus evidence or `none`.
5. The pane sends **one** update on the Operator bus.
6. If the operator must act, ask one question, then stop.

No fan-out. Many Agents or a Channel blast is a real side effect in the operator's chats and is not the default.

## Fictional illustration

- Pane: Atlas `00000000-0000-4000-8000-000000000001`
- Research owner: Nia `00000000-0000-4000-8000-000000000002`
- Implementation owner: Vega `00000000-0000-4000-8000-000000000003`

The operator asks Atlas. Atlas does not also message the non-owner.

## Do not

- Copy or invent a live team roster.
- Treat the pane as a second firm, desk, or program office.
- Post the same job to a Channel when a 1:1 owner exists.

## Related

- [docs/03-messaging.md](../docs/03-messaging.md)
- [examples/02-agent-to-agent.md](../examples/02-agent-to-agent.md)
- [boundaries/invariants.md](../boundaries/invariants.md) (I16)
