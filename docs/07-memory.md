# Memory

[Memory](../glossary.md) is durable notes the host injects on [Wake](04-turns-and-runtime.md). Tiers, most-specific wins:

1. Agent memory
2. Project memory
3. Shared user memory

## Agent memory

Private to that Agent. Other Agents do not read it.

Observed layout under the Agent folder:

```
<store>/agents/<uuid>/memory/
  profile.md
  log/YYYY-MM.md
```

`profile.md` is standing self-context. `log/YYYY-MM.md` is a monthly append log.

## Shared user memory

Shared across Agents, sharded **per writer**:

```
<store>/user-memory/by-agent/<uuid>/
```

Every file has one writer. Newest fact wins on conflict.

Given Atlas and Nia both write a fact about the same subject, when the host merges, then the newest write wins. Atlas does not edit Nia's shard.

## Project memory

Same shard pattern under the Project:

```
<store>/projects/<slug>/
```

An Agent joins a Project by listing the slug in `projects.json`:

```json
{
  "projects": ["atlas-notes"]
}
```

`atlas-notes` is fictional.

Not observed / not specified: a required filename set inside the Project shard beyond the shard-per-writer pattern.

## Precedence

On Wake, the host injects Memory with most-specific wins.

Given a fact exists in Atlas's Agent memory and a conflicting fact exists in shared user memory, when Atlas wakes, then Atlas's Agent memory wins.

Given a fact exists in Project memory and not in Agent memory, when the Agent has joined that Project, then Project memory wins over shared user memory.

## Writes

Memory writes are state, not messages. They do not appear on the Operator bus unless the Agent sends them.

Worked sequence: [examples/08-memory-write.md](../examples/08-memory-write.md).

## What Memory is not

- Not the sqlite transcript (`store.db`, `conversation-blobs.db`).
- Not `audit.jsonl`.
- Not a Skill body.
- Not a Routine prompt.
