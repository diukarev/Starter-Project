---
description: Pair this workspace for remote monitoring and steering from another device (phone or web).
---

# /remote-control

Make the current Conductor workspace reachable from another device so you can watch
progress and leave steering notes while you are away from your Mac.

Claude Code's built-in remote-control pairing is not yet surfaced inside Conductor
because the app owns the underlying session and renders its own chat UI (tracked
upstream in [meltylabs/conductor-releases#19](https://github.com/meltylabs/conductor-releases/issues/19)).
Until that lands, this command wires up an equivalent remote-monitoring loop with
what works today.

When invoked, do the following and nothing else:

1. If the working tree has uncommitted changes, commit them on the current branch
   with a concise message. If it is already clean, skip this step.
2. Pick a push target you can actually write to: prefer `origin`, but if the upstream
   is owned by someone else (no push access), push to the user's fork remote instead.
   Push the current branch and set its upstream.
3. Ensure a pull request exists for the branch against the repository's base branch —
   create one if it is missing, otherwise reuse the existing PR.
4. As the final message, print only:
   - the branch name and the remote it was pushed to,
   - the pull request URL,
   - one line: "Open this PR in the GitHub mobile app to follow progress, and comment
     on it to leave steering instructions for the next run."

Do not start any long-running work. This command only sets up remote visibility.
