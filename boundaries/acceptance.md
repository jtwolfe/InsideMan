# Acceptance

Checks an implementation must pass. Each check cites an invariant in [invariants.md](invariants.md). Examples use only Atlas, Nia, and Vega.

## Identity and delete

- Create Atlas, Nia, Vega with the fictional UUIDs. Rename Atlas's display name. UUID folder unchanged. (I1, I2)
- Sidebar right-click Delete on a throwaway Agent removes the Agent and transcript after confirm. Settings has no delete control. No archive. (I3)
- An Agent tool cannot delete a peer Agent or a Channel. (I4, I8)

## Channel

- Create `research-sync` with Atlas, Nia, Vega (3 members). Post succeeds for members. (I6, I7)
- Create with 7 UUIDs fails. (I5)
- Create without the creating Agent's UUID: creator cannot post. (I6)
- No `group.json` required in Agent folders. (I9)

## Operator bus

- Operator message to Atlas: first tool or action is a visible send. (I10)
- Model text omitted from send does not appear. (I11)
- A completed research result is sent, not only acknowledged. (I12)
- See [examples/01-operator-message-turn.md](../examples/01-operator-message-turn.md).

## Agent bus

- Atlas → Nia 1:1: Nia's Wake is a later Turn; no same-turn reply. (I13)
- 1:1 may include an image and `interrupt: true`. (I14)
- Channel post is text-only and wakes Atlas, Nia, and Vega. (I15)
- Default assignment is one owner. (I16)
- See [examples/02-agent-to-agent.md](../examples/02-agent-to-agent.md), [examples/03-channel-post.md](../examples/03-channel-post.md).

## Computers

- File written by Vega at `<agent-computer>/notes/plan.md` is readable by Atlas. (I17)
- Screenshot from Nia is Nia's Desktop, not Atlas's. (I18)
- No click / type / scroll API on the speaking Agent's Desktop. (I19)
- Operator-computer path rejected by Agent-computer tools. (I20)
- Copy both directions is verbatim. (I21)
- Login handoff: operator types the password on the Agent Desktop; Agent does not receive it; session remains. (I22)
- See [examples/04-desktop-login-handoff.md](../examples/04-desktop-login-handoff.md), [examples/05-copy-file-across-computers.md](../examples/05-copy-file-across-computers.md).

## Memory

- Conflicting Agent vs shared fact: Agent memory injected. (I23)
- Atlas writes only to Atlas's user-memory shard. (I24)
- Newer shard write wins. (I25)
- Joined Project beats shared user memory when Agent memory is silent. (I26)
- See [examples/08-memory-write.md](../examples/08-memory-write.md).

## Routines

- Document with cron + listeners rejected. (I27)
- Unspecified non-critical cron lands in weekday daytime `<operator-local>`. (I28)
- Finite watch stops at expiry. (I29)
- Slack listener silent for Channels the app is not in. (I30)
- See [examples/06-cron-routine.md](../examples/06-cron-routine.md), [examples/07-github-listener.md](../examples/07-github-listener.md).

## Skills and Connectors

- Follow path includes a Skill read in the same Turn. (I31)
- Service with a Connector is not opened in the browser first. (I32)
- Auth is a host card; no pasted link; no token in chat. (I33)
- New Plugin tools appear on the next message. (I34)
- See [examples/09-skill-follow.md](../examples/09-skill-follow.md), [skills/add-connector.md](../skills/add-connector.md).

## Workers and recovery

- Executor completion without an Agent send is not operator-visible. (I35)
- Second computerUse while one is active is rejected. (I36)
- Cloud coding agent default is remote branch + pull request, no clone. (I37)
- Update keeps files and logins. Reset is destructive. No third recovery path. (I38–I40)
