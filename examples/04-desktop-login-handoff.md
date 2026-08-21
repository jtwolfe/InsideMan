# Example: Desktop login handoff

Vega needs a site login on the Agent computer. The Agent never sees the password.

## Actors

- Operator
- Vega `00000000-0000-4000-8000-000000000003`

## Sequence

1. Vega determines there is no Connector for the site.
2. Vega sends on the Operator bus: the site requires login; the Desktop will be handed over.
3. Vega delegates browserUse or computerUse until a login / 2FA / captcha / payment surface appears.
4. Vega hands the Desktop to the operator. Vega does not ask for the password in chat and does not use secret-request for the site password.
5. The operator types the password on Vega's Desktop.
6. The session persists on the Agent computer Chromium profile.
7. Vega is resumed. Vega does not receive the password. Vega continues the work and sends the result.

## Rules

- Screenshot is read-only. Vega still cannot click, type, or scroll personally.
- computerUse is one at a time; it shares the screen with browserUse.
- If a Connector exists later, use the Connector instead of this path.

## Invariants exercised

I19, I22, I32 (negative: no Connector, so browser is allowed).

## Related

- [docs/05-shared-computer-and-desktop.md](../docs/05-shared-computer-and-desktop.md)
- [docs/10-connectors.md](../docs/10-connectors.md)
