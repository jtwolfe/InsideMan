# Connectors

A [Connector](../glossary.md) is the preferred path to an external service. It is an MCP server. Discover schema, then call.

If a Connector exists, do not browser-around it. Browser on the Agent computer is the fallback when no Connector exists.

## Vocabulary

Say **Connector** to the operator. "Plugin", "MCP server", and "plugin id" are plumbing.

A [Plugin](../glossary.md) is a marketplace bundle of Connectors and Skills, or a curated Connector. It lives on the operator's account.

## Auth

Auth is a connect card. The Agent never pastes authorization links into chat and never asks for tokens in chat. Use a secret-request card when a secret must be collected for messaging-channel credentials.

Plugin setup values (install fields) are not secret-request. Ask the operator for a value rather than guessing; do not invent it.

Given a Connector status is `needsAuth`, when the Agent starts auth, then the host authors the connect card. The Agent does not compose a connect card as message content.

The operator signs in. The Agent never sees the password.

## Discover then call

1. Discover the Connector's tool schema.
2. Call with arguments that match the schema.
3. On auth error, authenticate; do not retry the same unauthorized call unchanged.

Interfaces: [boundaries/interfaces.md](../boundaries/interfaces.md) — MCP: discover + call. Plugins: search / install / auth.

## Add flow

Product Skill: [skills/add-connector.md](../skills/add-connector.md).

Summary:

1. Identify the service.
2. Search the catalog.
3. Read plugin detail, confirm with a question widget, install on the next turn.
4. Authenticate via the host-authored card if needed.
5. If nothing matches, add a remote URL or local command only when the operator has that endpoint; otherwise say it is not available.

Newly installed tools and Skills become available on the **next** message, not the same one.

## Channels in the info pane

The per-Agent info pane lists Channels when a Channel Connector exists. Not observed / not specified: any other Connector list inside that pane. See [docs/12-application-ui.md](12-application-ui.md).

## Fallback

No Connector, no remote endpoint, no local command: tell the operator it is not available to connect. If the need is a website behind a login, use the Agent computer browser and, for login / 2FA / captcha / payment, hand the Desktop to the operator.
