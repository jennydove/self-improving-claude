# Settings Guide: Hooks and Automation

`settings.json` is how you wire up automated behaviors in Claude Code. There are two mechanisms: **hooks** (event-triggered) and **scheduled triggers** (time-triggered via `/schedule`).

---

## Hooks

Hooks run shell commands automatically in response to Claude Code events. They live in `.claude/settings.json`.

### Common hook events

**`PostToolUse`** — runs after a specific tool call completes.

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Write",
        "hooks": [
          {
            "type": "command",
            "command": "echo \"File written at $(date)\" >> .claude/session.log"
          }
        ]
      }
    ]
  }
}
```

**`Stop`** — runs when Claude finishes a response. Useful for end-of-session triggers.

```json
{
  "hooks": {
    "Stop": [
      {
        "hooks": [
          {
            "type": "command",
            "command": "echo 'Session complete' >> .claude/session.log"
          }
        ]
      }
    ]
  }
}
```

### Hook rules
- Hooks run every time the event fires — make sure commands are fast and idempotent
- Hook failures are logged but don't block Claude
- Use hooks for lightweight event-triggered automation; use `/schedule` for heavier recurring tasks

---

## Scheduled Triggers

Use the built-in `/schedule` skill to create remote triggers on a cron schedule. This is how you automate audits.

### Example: schedule weekly skill audit

```
/schedule
```

Then follow the prompts to set:
- Command: `/audit-skills`
- Schedule: `0 9 * * 1` (every Monday at 9am)
- Description: "Weekly skill quality audit"

### Example: schedule bi-weekly CLAUDE.md audit

```
/schedule
```

- Command: `/audit-claude-md`
- Schedule: `0 9 1,15 * *` (1st and 15th of each month at 9am)
- Description: "Bi-weekly CLAUDE.md health check"

---

## The Automation Playbook

Follow this staged approach — don't automate everything at once.

### Stage 1: Audits on schedule (start here)
Schedule `/audit-skills` and `/audit-claude-md` from the beginning. Audits are read-only — they produce reports, they don't change anything. Safe to automate immediately.

### Stage 2: Fix loop stays manual (first few weeks)
Review audit output yourself and run `/fix-skills` or `/fix-claude-md` manually. This lets you:
- See what the audits are flagging
- Verify the audit criteria match your actual standards
- Catch any over-aggressive or inaccurate findings before they cause automated changes

### Stage 3: Automate fixes (when you trust it)
Once audit output has been consistently accurate for several weeks, you can chain audit → fix automatically. Only do this when you're confident the audit is right more often than it's wrong.

A noisy audit running automated fixes will make your setup worse, not better.
