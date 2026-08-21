# Workers

A [Worker](../glossary.md) is a background actor with **no user voice**. The speaking Agent remains responsible for sending results on the Operator bus.

## Kinds

| Worker | Role |
| --- | --- |
| executor | General background worker. No user voice. |
| browserUse | Page-level browser. Preferred for web. |
| computerUse | GUI / Desktop / sites that defeat DOM automation. One at a time; they share the screen. |
| watchVideo / videoReview | Video analysis. |
| Cloud coding agent | Remote repository work on a branch + pull request. |

## Dispatch

Interfaces (not live IDs): task dispatch, check / message / stop, Cloud coding agent launch / reply.

Given Atlas dispatches an executor, when the executor finishes, then Atlas sends the result to the operator. The executor does not speak.

## browserUse and computerUse

They share the Agent Desktop. Only one interactive GUI Worker at a time.

- Prefer browserUse for page-level work.
- Use computerUse when DOM automation fails or the work is OS GUI.

The speaking Agent cannot click, type, or scroll the Desktop itself. Screenshot is read-only. See [docs/05-shared-computer-and-desktop.md](05-shared-computer-and-desktop.md).

## Cloud coding agent

Remote. Edits a GitHub repository on a branch and opens a pull request. Authentication is the signed-in operator's. Never ask for an API key.

Do not clone repositories onto the Agent computer or the Operator computer except when the operator explicitly asks or the work can only exist on that machine.

Launch and reply are the two host actions. A reply is queued until the current remote turn finishes unless interrupted.

## Video Workers

watchVideo / videoReview analyze video. Not observed / not specified: extra video Worker kinds.

## Executor

The Worker used by this specification's own authoring pattern: general background work, no user voice, results reported to the parent. In product terms, the speaking Agent still owes the operator a send.
