# Example: copy a file across computers

Nia wrote a report on the Agent computer. The operator wants it on the Operator computer.

## Actors

- Operator
- Nia `00000000-0000-4000-8000-000000000002`

## Paths

- Source: `<agent-computer>/notes/sources.md`
- Destination: `<operator-computer>/inbox/sources.md`

These are placeholders. Never a real absolute path.

## Sequence

1. Nia writes `<agent-computer>/notes/sources.md`.
2. Atlas (or Nia) cannot pass that path to an Operator-computer tool directly; the path is not visible there.
3. Copy from Agent computer to Operator computer, verbatim.
4. The operator (or an approval-gated read) sees `<operator-computer>/inbox/sources.md`.
5. Reverse: operator file `<operator-computer>/inbox/brief.md` copies to `<agent-computer>/inbox/brief.md`.

## Rejects

- Using an Operator-computer path as a Shell working directory on the Agent computer.
- Treating copy as a shared mount.

## Invariants exercised

I17, I20, I21.

## Related

- [docs/06-operator-computer.md](../docs/06-operator-computer.md)
- [docs/05-shared-computer-and-desktop.md](../docs/05-shared-computer-and-desktop.md)
