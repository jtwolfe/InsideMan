# Messaging

Two buses. Names match [glossary.md](../glossary.md).

## Operator bus

Operator ↔ Agent is the Agent's only user-visible voice.

Rules:

- Plain model text is not delivered.
- Delivery is an explicit send.
- The first action on a user-opened turn is a visible reply.
- Results must be sent, not only acknowledged.

User-voice surfaces (interfaces, not live IDs): send text, attachments, question widgets, secret-request, Cloud coding agent cards, emoji reaction on operator messages.

### First-action rule

Given the operator opened a turn with Atlas, when the Wake starts, then Atlas's first action is a visible send on the Operator bus.

Given Atlas finished a research handoff, when the work has a result, then Atlas sends the result. A silent acknowledgment is not delivery.

Worked sequence: [examples/01-operator-message-turn.md](../examples/01-operator-message-turn.md).

## Agent bus

Agent ↔ Agent, or a post to a Channel, is async and fire-and-forget. Address by UUID. Delivery wakes the target on a **later** turn. There is no reply in the same turn.

| Kind | Payload | Wake | Same-turn reply |
| --- | --- | --- | --- |
| 1:1 | Text; may carry images; may interrupt (priority) | Target Agent | No |
| Channel | Text only | Every member | No |

### Send-to-agent payload (fictional)

```json
{
  "to": "00000000-0000-4000-8000-000000000002",
  "from": "00000000-0000-4000-8000-000000000001",
  "text": "Please gather sources on the storage layout question.",
  "interrupt": false
}
```

`to` and `from` are Agent UUIDs. `interrupt: true` is priority on a 1:1. Channel posts do not carry images and do not interrupt a single target; they wake every member.

Worked sequences: [examples/02-agent-to-agent.md](../examples/02-agent-to-agent.md), [examples/03-channel-post.md](../examples/03-channel-post.md).

## Fan-out

Fan-out (many Agents or a group) is a real side effect in the operator's chats. Default is one owner, not a blast.

The user-authored routing Skill follows this pattern: the operator talks to one pane Agent; the pane routes to exactly one owner; the owner files a short report; no fan-out. See [skills/operator-routing-pane.md](../skills/operator-routing-pane.md).

Given the operator asked Atlas for research, when Atlas assigns the job, then Atlas sends to Nia only. Atlas does not also send the same job to Vega unless the operator was explicit.

## Channel membership and posting

Membership lets an Agent post. An Agent that is not a member cannot post. The creating Agent must include itself to participate.

Agents cannot delete Channels. The operator deletes from the sidebar.

## What is not a message

- Tool traces on a Turn are not operator-visible unless sent.
- Worker progress is not the user-visible voice. The owning Agent must send the result.
- Memory writes are not messages. See [docs/07-memory.md](07-memory.md).

## Related interfaces

[boundaries/interfaces.md](../boundaries/interfaces.md) — Team: create/update Agent, create/update Channel, send to Agent/Channel.
