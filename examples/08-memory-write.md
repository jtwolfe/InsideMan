# Example: Memory write

Atlas writes a standing preference. Nia writes a shared fact. Precedence is most-specific wins.

## Actor folders

- Atlas: `<store>/agents/00000000-0000-4000-8000-000000000001/`
- Nia: `<store>/agents/00000000-0000-4000-8000-000000000002/`

## Sequence

1. Atlas writes Agent memory (private):

   `<store>/agents/00000000-0000-4000-8000-000000000001/memory/profile.md`

   Fact: "Default to one owner. Do not fan out."

2. Nia writes shared user memory in Nia's shard only:

   `<store>/user-memory/by-agent/00000000-0000-4000-8000-000000000002/routing.md`

   Fact: "Research jobs go to Nia."

3. Atlas writes a later shared fact in Atlas's shard:

   `<store>/user-memory/by-agent/00000000-0000-4000-8000-000000000001/routing.md`

   Fact: "Research jobs go to Nia unless the operator names Vega."

4. On Atlas's next Wake, Agent memory (step 1) beats both shared facts for the fan-out rule.
5. For the research-owner fact, newest shared write wins: Atlas's shard (step 3).
6. Nia cannot write into Atlas's shard.

## Project memory

If Atlas has `projects.json` `{ "projects": ["atlas-notes"] }`, facts under `<store>/projects/atlas-notes/` beat shared user memory when Agent memory is silent.

## Invariants exercised

I23, I24, I25, I26.

## Related

- [docs/07-memory.md](../docs/07-memory.md)
- [docs/13-store-layout.md](../docs/13-store-layout.md)
