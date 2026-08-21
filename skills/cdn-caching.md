---
name: cdn-caching
description: Debug Vercel CDN caching, ISR/PPR, cacheReason, ppr_state, costs.
---

# cdn-caching

Use when cache hit rate, stale content, or revalidation is the question.

## Steps

1. Inspect cacheReason / ppr_state on the failing request before changing config.
2. Separate ISR/PPR behavior from Function-level caching.
3. Report cost impact if cache settings change.

## Related

- [catalog.md](catalog.md)
- [docs/09-skills.md](../docs/09-skills.md)
