# Operator computer

The [Operator computer](../glossary.md) is the human's machine. It is not the [Agent computer](05-shared-computer-and-desktop.md).

Placeholder root: `<operator-computer>/`.

## Bridge

Access from an Agent to the Operator computer is approval-gated.

Surfaces (interfaces, not live IDs):

- Approval-gated shell
- Approval-gated structured read
- Copy to the Agent computer
- Copy from the Agent computer

A path on one computer is not visible on the other. The Agent cannot pass an Operator-computer path to Agent-computer tools, or the reverse.

## Copy

Copy is verbatim. Any type or size. Binaries included.

| Direction | Meaning |
| --- | --- |
| Operator computer → Agent computer | Lands under `<agent-computer>/` at a chosen path, or a default intake directory. Not observed / not specified: the default intake name. |
| Agent computer → Operator computer | Lands under `<operator-computer>/` at a chosen path, or the current Operator-computer working directory. |

Worked sequence: [examples/05-copy-file-across-computers.md](../examples/05-copy-file-across-computers.md).

## Approvals

Given an Agent requests a shell on the Operator computer, when the host presents the command, then the command does not run until the operator approves.

Not observed / not specified: the exact approval-card layout beyond the fact that the bridge is approval-gated.

## Auth handoff is not Operator-computer work

Login, 2FA, captcha, and payment happen on the **Agent** Desktop. The operator is handed that Desktop. The Agent never sees the password. That sequence is [examples/04-desktop-login-handoff.md](../examples/04-desktop-login-handoff.md), not a copy of credentials onto the Operator computer.

## Routines and timezone

A cron [Routine](08-routines.md) uses the operator's local timezone, written `<operator-local>`. Never name a real timezone in this specification.

## What does not live here

The Store is not on the Operator computer. Agent folders, Memory shards, and sqlite transcripts live under `<store>/`. See [docs/13-store-layout.md](13-store-layout.md).
