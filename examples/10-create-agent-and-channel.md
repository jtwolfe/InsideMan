# Example: create Agent and Channel

The operator asks Atlas to add a specialist and a Channel. This example uses only the fictional three; treat Vega as the newly created specialist.

## Create Agent

Team surface: create / update Agent.

Resulting folder:

```
<store>/agents/00000000-0000-4000-8000-000000000003/
```

`profile.json`:

```json
{
  "name": "Vega",
  "description": "Implementation specialist.",
  "title": "Implementation",
  "avatarShape": "square",
  "avatarColor": "#E76F51"
}
```

`settings.json`:

```json
{
  "notifyOnAgentUpdates": true
}
```

Optional `avatar.png` beside the profile. Avatar is not a key inside `profile.json`.

Display name is not the key. A later rename leaves the UUID folder in place.

## Create Channel

Team surface: create / update Channel.

- Name: `research-sync`
- Members: Atlas, Nia, Vega (the creating Agent includes itself)

Cap 6. Channels do not nest. No `group.json` is required in Agent folders.

## After create

- Atlas can send Vega a 1:1 (Agent bus).
- Atlas can post text to `research-sync`.
- Atlas cannot delete Vega or the Channel. The operator deletes from the sidebar (right-click row, Delete, confirm).

## Invariants exercised

I1, I5, I6, I8, I9.

## Related

- [docs/02-identity.md](../docs/02-identity.md)
- [docs/13-store-layout.md](../docs/13-store-layout.md)
- [examples/03-channel-post.md](03-channel-post.md)
