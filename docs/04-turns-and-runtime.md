# Turns and runtime

The model is stateless per turn. Durable state is on disk. A [Wake](../glossary.md) is one model invocation. A [Turn](../glossary.md) is the span of that Wake, including tool calls, until the model stops.

The hard part of a rebuild is the Wake router: durable people, stateless turns.

## Wake injection

Each Wake injects:

1. **Profile** — `name`, `description`, `title`, `avatarShape`, `avatarColor` from `profile.json`. Avatar bytes are not in the JSON.
2. **Memory** — tiered; most-specific wins. See [docs/07-memory.md](07-memory.md).
3. **Teammate roster** — name + UUID + one-line brief.
4. **Tools** — the surfaces in [boundaries/interfaces.md](../boundaries/interfaces.md).
5. **Skills catalog** — name + description. An Agent must read a Skill body before following it. See [docs/09-skills.md](09-skills.md).

The Agent does not persist model weights. After the Turn ends, the next Wake is a new injection.

## User-opened turn

Given the operator sent a message to Atlas, when the host opens a Turn, then:

1. Atlas's first action is a visible reply on the Operator bus.
2. Tool work may follow.
3. Results must be sent, not only acknowledged.

See [examples/01-operator-message-turn.md](../examples/01-operator-message-turn.md).

## Agent-bus wake

Given Atlas sent a 1:1 to Nia, when delivery occurs, then Nia wakes on a **later** turn. Atlas does not receive Nia's reply in the same Turn. Nia may later send back on the Agent bus, which wakes Atlas on a subsequent Turn.

Interrupt (priority) is allowed on 1:1. Channel posts wake every member and are text-only.

## Routine wake

A [Routine](08-routines.md) opens a Turn with an intent prompt. The prompt is not a frozen tool recipe. Finite watches self-expire.

## Hosted runtime pieces

Describe generically. Do not pin a live host.

| Piece | Role |
| --- | --- |
| Desktop start/stop scripts | Bring a per-Agent Desktop up or down. |
| Window router | Table of Agent UUID → integer window id + opaque tokens. |
| Store-sync / transcript-mirror workers | Keep `<store>/` and transcripts consistent. |
| Chromium profile | On the Agent computer. Sessions persist across turns. |
| Health check | machine-id, Chrome, DNS, clock, D-Bus. |

Runtime may be local Docker or a brokered pod.

## Recovery

Only the paths in Settings → Updates. See [docs/12-application-ui.md](12-application-ui.md).

- **Update Grok Bot's Computer** — keeps files and logins, reinstalls software. Two-click confirm.
- **Reset Grok Bot's Computer** — last resort. Snapshot. Can lose unsynced work.

Do not invent other recovery paths.

## Workers on a Turn

The speaking Agent may dispatch a [Worker](11-workers.md). The Worker has no user voice. The speaking Agent remains responsible for sending the result on the Operator bus.

Cloud coding agent work happens on a remote branch + pull request. Do not clone repositories onto either computer except when the operator explicitly asks or the work can only exist on that machine.

## What the Agent cannot do on its Desktop

The Agent cannot click, type, or scroll its own Desktop. Screenshot is read-only. Interactive work is delegated. See [docs/05-shared-computer-and-desktop.md](05-shared-computer-and-desktop.md).
