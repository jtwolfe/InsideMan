---
name: learn-from-demonstration
description: Turn a screen-recorded demonstration on the agent computer into a reusable skill. Use when a teach recording finishes.
---

# Learn from a demonstration

The operator demonstrated a task on the Agent computer. A recording is available. Turn the demonstration into a reusable Skill. Work in the open: send a short acknowledgment that the demo is being watched, and narrate meaningful beats.

## Capture

The host finalizes the recording. Do not send stop signals to the capture process. Claim the oldest unprocessed recording for this Agent from the host-injected teach queue. Read session metadata from the claimed record, not from paths invented in the operator message.

Wait until the video file is complete before analysis. Use one foreground wait long enough for flush, rather than a poll loop.

## Watch

Use a video Worker (watchVideo / videoReview) to analyze the demonstration. Do not invent UI that was not in the recording.

## Write the Skill

Create a user Skill:

```yaml
---
name: <slug>
description: <one line: what it does and when to use>
---
```

Body: the demonstrated steps as an intent the next Agent can follow. Do not freeze tool IDs as if they were the only legal path. Do not copy operator passwords or secrets from the screen.

Save as a user-created Skill (writable). Managed and plugin Skills stay read-only.

## Report

Send the operator: Skill name, when to use, and where it lives. Offer one chance to correct the write-up.

## Related

- [docs/09-skills.md](../docs/09-skills.md)
- [docs/11-workers.md](../docs/11-workers.md)
