---
name: add-connector
description: Walk through connecting a new MCP connector. Search the catalog, install, and authenticate.
---

# Add a Connector

Help the operator connect a new [Connector](../docs/10-connectors.md) (an integration such as Linear, Notion, GitHub, or Slack). Say "Connector" to the operator. Plugin, MCP server, and plugin id are plumbing.

## 1. Identify the service

If the operator named a service, use that. If not, ask which service with one short send, then wait.

## 2. Search the catalog

Search Plugins with the service name. Read-only; no confirmation.

- Already installed: do not reinstall. If status is `needsAuth`, go to authentication. Otherwise tell the operator it is connected.
- Not installed: continue to install.
- Several plausible matches: question widget with real matches only. Never invent options.
- Nothing matches: go to "No catalog match".

## 3. Read detail, confirm, install

Read plugin detail before describing the install. Installing changes the operator's account, so confirm with a question widget (Yes / No). A question widget ends the Turn. Install on the next Turn after Yes.

Pass setup fields from the detail. Ask for any secret rather than guessing. Do not use secret-request for Plugin setup values (that card is for messaging-channel credentials).

Newly installed tools and Skills become available on the next message, not the same one.

## 4. Authentication

The connect card is host-authored. The Agent cannot compose one as message content.

Never paste an authorization link into chat. Never reach the same service another way while authorization is pending. After the card is up, finish unrelated work and end the Turn. The operator authorizes in place.

## 5. No catalog match

- Remote MCP HTTPS URL from the service docs: confirm, then add. Do not embed credentials in the URL.
- Local command (`npx` / `uvx`): add as a command on the Agent computer. The same command is shared by the operator's other Agents; say that when confirming.
- No Connector, no endpoint, no command: say it is not available. A website behind a login can use the Agent computer browser instead.

## Wrap up

Send a short confirmation. Offer one concrete next action the new Connector enables.

## Related

- [docs/10-connectors.md](../docs/10-connectors.md)
- [examples/09-skill-follow.md](../examples/09-skill-follow.md)
