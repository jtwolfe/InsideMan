# Example: operator message turn

The operator opens a Turn with Atlas. Atlas is the pane Agent.

## Actors

- Operator
- Atlas `00000000-0000-4000-8000-000000000001`

## Sequence

1. The operator sends: "What is in the Store under an Agent folder?"
2. The host opens a Wake. Injection: Atlas profile, Memory, roster (Atlas / Nia / Vega), tools, skills catalog.
3. Atlas's first action is a visible send on the Operator bus: a short acknowledgment that the question was received and that the answer is the Agent-folder layout.
4. Atlas may read [docs](../docs/13-store-layout.md) facts from Memory or tools.
5. Atlas sends the result: `profile.json`, `settings.json`, optional avatar, sqlite pair, `audit.jsonl`, optional `memory/`, `automations/`, `attachments/`, `assets/`, `projects.json`, `enabled-workflows.json`.
6. A silent internal summary is not delivery. The send in step 5 is required.

## Invariants exercised

I10, I11, I12. See [boundaries/invariants.md](../boundaries/invariants.md).

## Related

- [docs/03-messaging.md](../docs/03-messaging.md)
- [docs/04-turns-and-runtime.md](../docs/04-turns-and-runtime.md)
