# Example: GitHub listener

Vega reviews new pull requests. Listeners only. No cron on this Routine.

## Document

```json
{
  "name": "pr-review-watch",
  "agent": "00000000-0000-4000-8000-000000000003",
  "trigger": {
    "kind": "listeners",
    "listeners": [
      {
        "service": "GitHub",
        "event": "pull_request",
        "repo": "<owner>/<repo>"
      }
    ]
  },
  "prompt": "When a pull request opens, review the diff and file a short report to Atlas."
}
```

`<owner>/<repo>` is a placeholder, not a live project slug.

## Sequence

1. The operator connects GitHub (Connector + connect card). Vega does not ask for a token in chat.
2. The operator creates the listener Routine on Vega.
3. A pull-request event arrives on the connected account.
4. Vega wakes with the intent prompt.
5. Vega uses the GitHub Connector (not the browser).
6. Vega sends Atlas a 1:1 report (`result` / `decision` / `blocker`). Atlas sends the operator if the pane should speak.

## Finite watch

If the operator asked to watch "the next pull request only", the Routine self-expires after that event.

## Rejects

- Cron + this listener on the same Routine.
- Browser-around GitHub while the Connector exists.

## Invariants exercised

I27, I29, I32, I33.

## Related

- [docs/08-routines.md](../docs/08-routines.md)
- [docs/10-connectors.md](../docs/10-connectors.md)
