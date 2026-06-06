# Beeper v2 — Claude Code plugin

Cross-Claude task delegation, cloud-hosted. Async, allowlist-gated, SMS-notified.

## Install

1. Ask admin (Chinat) to add you to the allowlist via the host's `/admin` page.
2. In Claude Code, add the marketplace and install (one-time):
   ```
   /plugin marketplace add edumame/beeper-v2
   /plugin install beeper-v2
   ```
3. Add to your `~/.zshenv`:
   ```bash
   export BEEPER_USER=<your-id>       # e.g. edward, kaan, chinat, jeffrey
   export BEEPER_API_URL=https://beeper-v2-host.vercel.app
   ```
4. `source ~/.zshenv`, restart your Claude Code session. Done — `/beeper-v2` is now a slash command.

## Use

- `/beeper-v2` — check your queue
- `/beeper-v2 send <to> "task"` — send a beep
- `/beeper-v2 reply <id> "text"` — reply to a beep
- `/beeper-v2 decline <id> "reason"` — decline a beep

Or just say it: "ask Edward's Claude what's in judges_v2", "beep Kaan about the demo bug", "what's queued for me?".

## How it works

The plugin is a thin Claude Code skill that calls a private cloud service. The server owns the queue (InsForge), the SMS provider (Twilio), and the audit log. You don't need any provider credentials — only `BEEPER_USER` and `BEEPER_API_URL`.

## Trust model

- **Allowlist** is the only sender gate. Mutual: to beep someone, they must add you.
- **Recipient always confirms** in Claude before executing a beep.
- **No auto-execute**, ever. The skill prompts execute / reply / decline for every queued beep.

## Source

- Plugin (this repo): https://github.com/edumame/beeper-v2
- Host: https://github.com/edumame/beeper-v2-host (private)
