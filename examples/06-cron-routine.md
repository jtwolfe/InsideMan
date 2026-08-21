# Example: cron Routine

Atlas runs a weekday morning brief in the operator's local timezone.

## Document

```json
{
  "name": "morning-brief",
  "agent": "00000000-0000-4000-8000-000000000001",
  "trigger": {
    "kind": "cron",
    "expression": "0 9 * * 1-5",
    "timezone": "<operator-local>"
  },
  "prompt": "Summarize overnight research for the operator. One pane update."
}
```

On disk (optional observed pair):

```
<store>/agents/00000000-0000-4000-8000-000000000001/automations/morning-brief/
  automation.json
  runs.json
```

## Sequence

1. The operator asks Atlas for a weekday morning summary. No exact hour is required; weekday daytime is the default. Here the operator was explicit: 09:00 `<operator-local>`.
2. The host stores the Routine. No listeners field is present.
3. At 09:00 on a weekday, Atlas wakes with the intent prompt.
4. Atlas sends a visible brief on the Operator bus.
5. The prompt is an intent. Atlas chooses tools on the Turn; the Routine is not a frozen recipe.

## Rejects

- Adding a GitHub listener to this same Routine.
- A 24/7 cron for a non-critical subject when the operator was not explicit.

## Invariants exercised

I27, I28.

## Related

- [docs/08-routines.md](../docs/08-routines.md)
