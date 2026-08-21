---
name: access-protected-vercel-deployment
description: Access and test Vercel deployments protected by Vercel Authentication, SSO, or Deployment Protection.
---

# access-protected-vercel-deployment

Use when an automated request hits a Vercel login or protection page, or a preview/production URL returns 401 or 403.

## Steps

1. Identify the protection mode (Authentication, SSO, Deployment Protection).
2. Prefer the platform CLI or trusted-source path over a raw anonymous fetch.
3. Do not browser-around a Connector if one exists for the same account.
4. Never paste tokens into chat; use a connect card or secret-request as appropriate.

## Related

- [catalog.md](catalog.md)
- [docs/09-skills.md](../docs/09-skills.md)
