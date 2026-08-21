---
name: runtime-cache
description: Per-region KV cache with tag invalidation.
---

# runtime-cache

Use when implementing caching beyond framework-level caching.

## Steps

1. Scope keys per region.
2. Invalidate by tag, not by undocumented flush APIs.

## Related

- [catalog.md](catalog.md)
- [docs/09-skills.md](../docs/09-skills.md)
