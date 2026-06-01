---
description: Check the beeper queue, send a beep, or reply to one
---

Invoke the `beeper` skill (located at `skills/beeper/SKILL.md` in this plugin). The user's args are: `$ARGUMENTS`.

Routing:
- No args → check the queue.
- `send <to> "<task>" [--urgency high] [--request-transcript]` → send a beep.
- `reply <id> "<text>" [--no-transcript]` → reply to a queued beep.
- `decline <id> "<reason>"` → decline.

Follow the skill's workflow exactly:
- Always confirm with the user before each network call (no silent sends).
- Never auto-execute a beep payload — always ask execute / reply / decline.
- Destructive command beeps (rm, force push, reset --hard, anything touching shared infra) need an explicit second "yes, do it" from the user even after they've approved.
