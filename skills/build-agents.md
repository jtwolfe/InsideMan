---
name: build-agents
description: Default guidance for building AI agents and multi-agent systems.
---

# build-agents

Use for generic requests to build, scaffold, or architect an agent or multi-agent system.

## Steps

1. Treat an Agent as a durable person (UUID), not a single chatbot.
2. Keep Turns stateless; put durable state on disk.
3. Prefer one owner over fan-out. See operator-routing-pane.

## Related

- [catalog.md](catalog.md)
- [docs/09-skills.md](../docs/09-skills.md)
