---
name: bootstrap
description: Bootstrapping repos that depend on Vercel-linked resources (databases, auth, managed integrations).
---

# bootstrap

Use when setting up or repairing a repository so linking, env pulls, and first-run commands happen in a safe order.

## Steps

1. Link the project before pulling environment values.
2. Provision managed resources, then pull env, then run first-run db/dev commands.
3. Do not clone onto either computer unless the operator asked or the work can only exist there.

## Related

- [catalog.md](catalog.md)
- [docs/09-skills.md](../docs/09-skills.md)
