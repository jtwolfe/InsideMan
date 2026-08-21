# Shared computer and Desktop

Two facts that must not be collapsed:

1. The [Agent computer](../glossary.md) is **one** Linux machine shared by **all** of the operator's Agents.
2. A [Desktop](../glossary.md) is **per-Agent**, not per-machine.

Agents share the computer. They do not share Desktops.

## Agent computer

- One Linux machine.
- Same filesystem, installed tools, and browser logins for every Agent.
- Persistent across turns. Files, installed tools, and browser logins remain.
- Nothing on the Agent computer is the [Operator computer](06-operator-computer.md).

Placeholder root: `<agent-computer>/`.

A path on the Agent computer is not visible on the Operator computer. Copy is explicit. See [examples/05-copy-file-across-computers.md](../examples/05-copy-file-across-computers.md).

## Desktop

- Private screen, about 1280x800.
- An Agent cannot see another Agent's Desktop.
- The Agent cannot click, type, or scroll its own Desktop.
- Screenshot is read-only.

Given Atlas and Nia share the Agent computer, when Atlas screenshots, then the image is Atlas's Desktop only. Nia's screen is not in the frame.

## Interactive work

Delegated. The speaking Agent does not drive its own Desktop.

| Worker | Use |
| --- | --- |
| browserUse | Page-level browser. Preferred. |
| computerUse | GUI / Desktop / sites that defeat DOM automation. One at a time; they share the screen. |

Login, 2FA, captcha, and payment: hand the Desktop to the operator. The Agent never sees the password. The session persists on the Agent computer after the operator finishes.

Worked sequence: [examples/04-desktop-login-handoff.md](../examples/04-desktop-login-handoff.md).

## Window router

The host keeps a table of Agent UUID to integer window id, plus opaque tokens. Describe the table, not live values.

| Field | Meaning |
| --- | --- |
| Agent UUID | Canonical identity. |
| window id | Integer. Host-assigned. Not documented as a live number. |
| token | Opaque. Not a secret to paste into chat. |

Do not log or publish live window ids or tokens.

## Chromium profile

A Chromium profile lives on the Agent computer. Browser logins persist across turns and are shared by Agents on that machine (same profile store on the shared filesystem). Each Agent's Desktop is still a private screen.

If a Connector exists for a service, do not browser-around it. Browser on the Agent computer is the fallback when no Connector exists. See [docs/10-connectors.md](10-connectors.md).

## Health check

Generic host health: machine-id, Chrome, DNS, clock, D-Bus. Not observed / not specified: the on-screen placement of a health panel.

## Recovery

Settings → Updates → **Update Grok Bot's Computer** (keeps files and logins, reinstalls software). **Reset** is last resort (snapshot, can lose unsynced work). Do not invent other recovery paths. See [docs/12-application-ui.md](12-application-ui.md).
