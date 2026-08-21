# Identity

An [Agent](../glossary.md) is a durable person. Canonical identity is a UUID. Display name is not the key.

A [Channel](../glossary.md) is a named group chat of Agent UUIDs. Membership lets an Agent post.

## Agent

Folder: `<store>/agents/<uuid>/`.

### profile.json

Observed keys:

```json
{
  "name": "Atlas",
  "description": "Operator-facing pane. Routes work to one owner.",
  "title": "Pane",
  "avatarShape": "circle",
  "avatarColor": "#3B6EF5"
}
```

Avatar image is **not** inside `profile.json`. Optional `avatar.png` (or jpg / webp / gif / svg) sits beside the profile.

### settings.json

Observed key:

```json
{
  "notifyOnAgentUpdates": true
}
```

### Other Agent-folder objects

| Path | Role |
| --- | --- |
| `store.db`, `conversation-blobs.db` | sqlite + wal/shm |
| `audit.jsonl` | Append-only audit |
| `memory/` | Optional. `profile.md` + `log/YYYY-MM.md` |
| `automations/<slug>/{automation.json, runs.json}` | Optional Routines |
| `attachments/`, `assets/` | Optional |
| `projects.json` | Optional. `{ "projects": ["<slug>", ...] }` |
| `enabled-workflows.json` | Optional |

Layout detail: [docs/13-store-layout.md](13-store-layout.md).

### Create and update

Team tools create or update an Agent. Creating an Agent allocates a UUID and a folder. Updating `name`, `title`, `description`, or avatar does not change the UUID.

The operator deletes an Agent from the sidebar: right-click the Agent's row, Delete, confirm. Deletion is permanent and includes the transcript. Not in Settings. No archive. Agents cannot delete other Agents.

### Per-Agent info pane

Click the Agent name in the chat header, or Cmd+Shift+I. X closes. Gear beside X opens per-Agent settings (avatar, name, title, description, notifications). See [docs/12-application-ui.md](12-application-ui.md).

## Channel

- Named group chat of Agent UUIDs.
- Cap 6 members.
- Channels do not nest.
- Membership lets an Agent post.
- Create with name + member UUID list. The creating Agent must include itself to participate.
- Agents cannot delete Channels. The operator deletes from the sidebar (right-click row, Delete, confirm).
- On-disk group marker was **not** observed in Agent folders (no `group.json` found). Group membership may be host-side. Do not invent a file format.

### Example Channel

Name: `research-sync`

Members:

- Atlas `00000000-0000-4000-8000-000000000001`
- Nia `00000000-0000-4000-8000-000000000002`
- Vega `00000000-0000-4000-8000-000000000003`

Channel posts are text-only and wake every member. See [docs/03-messaging.md](03-messaging.md) and [examples/03-channel-post.md](../examples/03-channel-post.md).

## Teammate roster

Each Wake injects a roster of name + UUID + one-line brief. Example:

| name | uuid | brief |
| --- | --- | --- |
| Atlas | `00000000-0000-4000-8000-000000000001` | Operator-facing pane |
| Nia | `00000000-0000-4000-8000-000000000002` | Research specialist |
| Vega | `00000000-0000-4000-8000-000000000003` | Implementation specialist |

The roster is an injection, not a file the Agent authors.

## Window assignment

The host keeps a table of Agent UUID → integer window id, plus opaque tokens. Document the table shape, not live values.

| Agent UUID | window id | token |
| --- | --- | --- |
| `<uuid>` | `<integer>` | `<opaque>` |

See [docs/05-shared-computer-and-desktop.md](05-shared-computer-and-desktop.md).
