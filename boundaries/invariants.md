# Invariants

Every rule is testable: Given A, when B, then C. Terms match [glossary.md](../glossary.md).

## Identity

1. Given an Agent folder `<store>/agents/<uuid>/`, when `profile.json` `name` changes, then the UUID and folder name stay the same.
2. Given Atlas `00000000-0000-4000-8000-000000000001`, when another Agent is created with display name Atlas, then the new Agent receives a different UUID.
3. Given an Agent, when the operator deletes it, then deletion is from the sidebar (right-click row, Delete, confirm), the transcript is removed, and there is no archive. Settings is not the delete path.
4. Given an Agent, when a peer Agent attempts to delete it, then the delete fails.

## Channel

5. Given a Channel create call, when the member list has more than 6 UUIDs, then create fails.
6. Given Atlas creates a Channel, when Atlas omits its own UUID, then Atlas cannot post in that Channel.
7. Given a Channel, when a non-member sends a Channel post, then delivery is rejected.
8. Given a Channel, when an Agent attempts to delete it, then the delete fails. The operator deletes from the sidebar.
9. Given Agent folders, when inspected for `group.json`, then no on-disk group marker is required. Membership may be host-side.

## Messaging

10. Given a user-opened Turn, when the Wake starts, then the Agent's first action is a visible send on the Operator bus.
11. Given model text that was not passed to send, when the Turn ends, then the operator does not see that text.
12. Given work produced a result, when the Agent only acknowledges internally, then the operator has not received the result.
13. Given Atlas sends a 1:1 to Nia, when delivery occurs, then Nia wakes on a later Turn. Atlas does not receive a same-turn reply.
14. Given a 1:1, when `interrupt` is true, then the send is priority. Channel posts do not use 1:1 interrupt.
15. Given a Channel post, when it is accepted, then the payload is text-only and every member is woken.
16. Given the operator asked for one owner's work, when the pane Agent assigns the job, then exactly one Agent is messaged. Fan-out is not the default.

## Computers and Desktop

17. Given any of the operator's Agents, when they write a file on the Agent computer, then the file is visible to the other Agents on that machine.
18. Given Atlas's Desktop, when Nia requests a screenshot, then Nia does not receive Atlas's screen.
19. Given an Agent, when it attempts to click, type, or scroll its own Desktop, then the action is not available. Screenshot is read-only.
20. Given a path on the Operator computer, when an Agent-computer tool is pointed at that path, then the path is not visible.
21. Given a copy request, when it completes, then bytes on the destination match the source and the other computer's filesystem did not become a mount of the first.
22. Given login, 2FA, captcha, or payment, when credentials are needed, then the Desktop is handed to the operator and the Agent does not see the password. The session persists afterward.

## Memory

23. Given a fact in Agent memory and a conflicting fact in shared user memory, when that Agent wakes, then Agent memory wins.
24. Given shared user memory, when Atlas writes, then the write lands under `<store>/user-memory/by-agent/00000000-0000-4000-8000-000000000001/` and Nia does not write into Atlas's shard.
25. Given two shards that conflict, when the host merges, then the newest fact wins.
26. Given Project memory and no Agent-memory fact, when the Agent has joined that Project, then Project memory wins over shared user memory.

## Routines

27. Given a Routine document, when it contains both a cron schedule and listeners, then the document is invalid.
28. Given no explicit time window and a subject that is not time-critical, when a cron Routine is created, then the window is weekday daytime in `<operator-local>`.
29. Given a finite watch Routine, when its watch expires, then it does not keep firing.
30. Given a Slack Channel listener, when the Slack app is not in that Channel, then the Routine does not hear it.

## Skills and Connectors

31. Given a Skill in the catalog, when the Agent follows it, then the Agent read the Skill body in the current Turn first.
32. Given a Connector for a service, when the Agent needs that service, then the Agent uses the Connector and does not browser-around it.
33. Given Connector auth, when a connect card is required, then the host authors the card. The Agent does not paste an authorization link into chat and does not ask for tokens in chat.
34. Given a newly installed Plugin, when tools and Skills are needed, then they are available on the next message, not the same one.

## Workers

35. Given a Worker finishes, when the operator must see the outcome, then the speaking Agent sends it. The Worker has no user voice.
36. Given browserUse or computerUse, when one is active, then a second interactive GUI Worker is not started on the same Desktop.
37. Given Cloud coding agent work, when the operator did not ask to clone and the work can exist remotely, then neither computer receives a clone.

## Runtime

38. Given Update Grok Bot's Computer, when it completes, then files and logins remain and software is reinstalled.
39. Given Reset Grok Bot's Computer, when the operator confirms, then the action is destructive and unsynced work may be lost.
40. Given a recovery need, when neither Update nor Reset is the path, then no other recovery path is specified.
