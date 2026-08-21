---
name: auth
description: Clerk, Descope, and Auth0 setup for Next.js. Middleware auth, sign-in/sign-up, Marketplace provisioning.
---

# auth

Use when implementing user authentication on Next.js.

## Steps

1. Pick the provider the operator named (Clerk, Descope, Auth0).
2. Wire middleware and sign-in/sign-up; do not invent extra Settings screens.
3. Login for third-party consoles still uses Desktop handoff; the Agent never sees the password.

## Related

- [catalog.md](catalog.md)
- [docs/09-skills.md](../docs/09-skills.md)
