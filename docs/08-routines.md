# Routines

A [Routine](../glossary.md) is a standing order. It opens a [Wake](04-turns-and-runtime.md) with an intent prompt.

The prompt is an intent, not a frozen tool recipe. Finite watches self-expire.

## Trigger: one kind, never both

A Routine has **either**:

- a cron schedule in the operator's local timezone (`<operator-local>`), **or**
- event listeners

Never both schedule and listener on one Routine.

### Cron

Weekday daytime is the default window unless the operator was explicit or the subject is truly time-critical / life-hours.

Fictional Routine document:

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

Worked sequence: [examples/06-cron-routine.md](../examples/06-cron-routine.md).

### Listeners

Event listeners use the operator's connected accounts. Observed listener families: Slack, GitHub, Microsoft Teams, Linear, Sentry, PagerDuty, webhook, or a group of listeners.

A Slack channel listener only hears channels the Slack app is in.

Fictional GitHub listener:

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

Worked sequence: [examples/07-github-listener.md](../examples/07-github-listener.md).

## On-disk

Optional under the Agent folder:

```
<store>/agents/<uuid>/automations/<slug>/
  automation.json
  runs.json
```

Do not invent keys beyond `automation.json` and `runs.json` as the observed pair.

## Skills

A Routine may point at a [Skill](09-skills.md). The Agent must still read the Skill before following it.

## Visibility

Per-Agent info pane includes Routines. Open the pane from the Agent name in the chat header or Cmd+Shift+I. See [docs/12-application-ui.md](12-application-ui.md).

## Invariants

Given a Routine document contains a cron expression, when it also lists listeners, then the document is invalid.

Given the operator did not name a time window and the subject is not time-critical, when a cron is created, then the window is weekday daytime in `<operator-local>`.
