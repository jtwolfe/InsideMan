# Example: Agent to Agent

Atlas routes research to Nia. One owner. No fan-out. No same-turn reply.

## Actors

- Atlas `00000000-0000-4000-8000-000000000001`
- Nia `00000000-0000-4000-8000-000000000002`

## Payload

```json
{
  "to": "00000000-0000-4000-8000-000000000002",
  "from": "00000000-0000-4000-8000-000000000001",
  "text": "Please gather sources on the Store layout question. File a short report: result / decision / blocker.",
  "interrupt": false
}
```

## Sequence

1. Operator asks Atlas for sources.
2. Atlas sends a visible reply on the Operator bus: Nia owns research.
3. Atlas sends the payload above on the Agent bus.
4. Atlas's Turn ends. Nia does not reply in this Turn.
5. Later, Nia wakes. Injection includes the message from Atlas.
6. Nia does the research and sends a 1:1 back to Atlas (later Turn for Atlas).
7. Atlas sends the operator the report.

Optional: `interrupt: true` if the operator's ask is priority. Images are allowed on 1:1.

## Invariants exercised

I13, I14, I16.

## Related

- [docs/03-messaging.md](../docs/03-messaging.md)
- [skills/operator-routing-pane.md](../skills/operator-routing-pane.md)
