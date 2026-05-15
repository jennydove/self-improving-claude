Update `.claude/settings.json` to configure hooks, automated behaviors, and scheduled tasks.

## When to run
- When adding a new automated behavior ("from now on, always do X after Y")
- When setting up or modifying scheduled audit runs
- When a hook is producing unexpected behavior and needs adjustment

## Key concepts

### Hooks
Hooks are shell commands that run automatically in response to Claude Code events. They live in `settings.json` under `hooks`. Common events:
- `PostToolUse` — runs after a tool call completes
- `Stop` — runs when Claude finishes a response

Example: automatically run `/update-memory` after every session by hooking the Stop event.

### Scheduled triggers
The built-in `/schedule` skill creates remote triggers that run commands on a cron schedule. Use this for:
- Weekly `/audit-skills` runs
- Bi-weekly `/audit-claude-md` runs
- Any recurring task that should happen without a prompt

See README for the automation playbook — schedule audits first, then add fix automation only once audits are accurate.

## Process

1. **Identify what needs to change**
   - What behavior should be automated?
   - Should it be a hook (event-triggered) or a schedule (time-triggered)?

2. **Read the current `settings.json`**

3. **Propose the change** with explanation of what will trigger and what will run

4. **Show the proposed JSON diff** and ask for approval before writing

5. **After writing**, confirm the behavior works as expected

## Important
- Never modify settings.json without showing the proposed change first
- Hooks run every time the event fires — make sure the hook command is idempotent and fast
- Use `/schedule` for time-based automation, hooks for event-based automation
