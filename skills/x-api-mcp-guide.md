---
name: x-api-mcp-guide
description: Read before using any X connection or on any X error. Estimate cost of each X call and confirm.
---

# X MCP guide

Read this Skill in the current Turn before calling any X Connector tool, and again on any X error.

The operator taps Connect and signs in with X. The Agent does not set up an API app, ask for keys, or tell the operator to create a Project or Production environment.

## On connect

The first time X is connected in a session, send capabilities once (adapt voice, keep the content):

- Account: profile, home timeline, posts, mentions
- Posts: open a post from a link; likes, reposts, quotes
- Users: look up by handle, search, read posts
- Search: posts and volume
- News and trends
- Bookmarks and folders

Requests use credits. Estimate cost before anything expensive and confirm with the operator.

If the first message is already an ask, send capabilities first, then do the ask. Once per session, not every message.

## Errors

On a core error, stop. Name the simple issue, then the next step. Do not explain enrollment mechanics or billing internals. Never retry 401, enrollment-blocked, or credits-blocked calls unchanged. Never ask for keys.

## Related

- [docs/10-connectors.md](../docs/10-connectors.md)
