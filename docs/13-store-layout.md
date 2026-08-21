# Store layout

The [Store](../glossary.md) is durable on-disk state. Root: `<store>/`. This is product layout, not a live host path.

## Tree

```
<store>/
  agents/
    <uuid>/
      profile.json
      settings.json
      avatar.png                 # optional; jpg/webp/gif/svg also allowed
      store.db                   # sqlite + wal/shm
      conversation-blobs.db      # sqlite + wal/shm
      audit.jsonl
      memory/                    # optional
        profile.md
        log/YYYY-MM.md
      automations/               # optional
        <slug>/
          automation.json
          runs.json
      attachments/               # optional
      assets/                    # optional
      projects.json              # optional
      enabled-workflows.json     # optional
  user-memory/
    by-agent/
      <uuid>/                    # one writer per shard
  projects/
    <slug>/                      # same shard pattern as user-memory
```

## Agent folder

Canonical identity is the UUID directory name, not `profile.json` `name`.

### profile.json

```json
{
  "name": "Nia",
  "description": "Research specialist.",
  "title": "Research",
  "avatarShape": "hexagon",
  "avatarColor": "#2A9D8F"
}
```

Avatar is a sibling file, not a field inside `profile.json`.

### settings.json

```json
{
  "notifyOnAgentUpdates": false
}
```

Only `notifyOnAgentUpdates` is documented as observed.

### projects.json

```json
{
  "projects": ["atlas-notes"]
}
```

### Databases

`store.db` and `conversation-blobs.db` are sqlite, with wal/shm sidecars. Not observed / not specified: table schemas.

### audit.jsonl

Append-only. Not observed / not specified: line schema.

## Channel membership

On-disk group marker was **not** observed in Agent folders (no `group.json` found). Group membership may be host-side. Do not invent a file format.

## Memory shards

- Agent memory: `<store>/agents/<uuid>/memory/` — private.
- Shared user memory: `<store>/user-memory/by-agent/<uuid>/` — one writer per shard; newest fact wins.
- Project memory: `<store>/projects/<slug>/` — same shard pattern.

See [docs/07-memory.md](07-memory.md).

## What is not in the Store

- Operator-computer files
- Agent-computer scratch that has not been written to `<store>/`
- Window-router live ids and tokens
- Connector secrets (auth is a connect card, not a file in the Agent folder)

## Fictional Agents in examples

| Directory | Agent |
| --- | --- |
| `<store>/agents/00000000-0000-4000-8000-000000000001/` | Atlas |
| `<store>/agents/00000000-0000-4000-8000-000000000002/` | Nia |
| `<store>/agents/00000000-0000-4000-8000-000000000003/` | Vega |
