# Setup Guide

> **If you're Claude:** This file is your implementation guide. Read it before doing anything else. Follow the steps in order.
>
> **If you're a human:** This walks you (and Claude) through adapting this template to your actual setup. Work through it together in a Claude Code session.

---

## What "implemented" looks like

Setup is complete when:
- [ ] `CLAUDE.md` reflects your actual project, tools, and role — no placeholder text remains
- [ ] `memory/MEMORY.md` is wired up and loading correctly
- [ ] `docs/standards-claude-md.md` and `docs/standards-skills.md` match your standards (or you've confirmed the defaults are fine)
- [ ] You've run `/today` and `/done` at least once
- [ ] `/audit-skills` has been run and any obvious issues are noted

---

## Step 1: Ask the user these questions

Work through these one at a time. You need the answers before editing any files.

1. **What is this project?** What will you primarily use Claude for here — task management, writing, research, client work, something else?
2. **What is Claude's role?** Should Claude make decisions independently in this context, or check in frequently? What does "good work" look like?
3. **What tools and integrations do you use?** (e.g. Todoist, Google Calendar, Slack, Notion, GitHub) For each: any constraints or conventions Claude should know?
4. **What's your name?** (Used in CLAUDE.md to replace `[name]` — avoids pronoun ambiguity)
5. **Do you have a GitHub sync configured?** Should `/today` pull config and `/done` push it?
6. **Any conventions or "never do this" rules?** Things Claude should always or never do in this project?

---

## Step 2: Fill in CLAUDE.md

Edit `CLAUDE.md` using the answers above. Replace every `[placeholder]` with real content. When done, the file should:
- Have no bracket placeholders remaining
- Describe a real project with a specific purpose
- List only the integrations actually in use
- Have a Claude's Ongoing Role section that's specific, not generic

If an optional section doesn't apply (e.g. no integrations yet), remove it rather than leaving it blank.

---

## Step 3: Wire up the memory system

The memory system only works if `memory/MEMORY.md` is loaded into every session.

Add this line to `CLAUDE.md` under a `## Memory` section:

```
Claude should load `memory/MEMORY.md` at the start of every session and treat the linked files as persistent context.
```

Then confirm the `memory/` directory exists (it does in this template). The `memory/examples/` files show the correct format — delete them once you've created your first real memory files.

---

## Step 4: Review the standards docs

Read `docs/standards-claude-md.md` and `docs/standards-skills.md`.

- If the defaults look right, leave them as-is.
- If your standards differ (e.g. you score skills differently, or have additional CLAUDE.md requirements), edit them now — before running any audits.

The audits are only as good as the standards they check against.

---

## Step 5: Run the first session

Open Claude Code in this project directory and run:

```
/today
```

Claude will surface tasks and priorities. At the end of the session, run:

```
/done
```

Claude will log what happened, update memory, and check for new skills.

---

## Step 6: First audit

After your first week, run:

```
/audit-skills
/audit-claude-md
```

Review the output. If findings look accurate, good — these are now your baseline. If findings are wrong or noisy, adjust `docs/standards-skills.md` or `docs/standards-claude-md.md` before scheduling anything.

---

## Step 7: Schedule audits

Once audit output looks right, schedule them to run automatically using the built-in `/schedule` skill:

- `/audit-skills` — weekly (suggested: Monday morning)
- `/audit-claude-md` — bi-weekly

See `docs/settings-guide.md` for the full automation playbook. **Do not automate fix commands until audits have been accurate for several weeks.**

---

## Ongoing: the self-improvement loop

From here, the system runs itself with light oversight:

| When | What to do |
|---|---|
| Start of session | `/today` |
| End of session | `/done` |
| Weekly (automated) | `/audit-skills` |
| Bi-weekly (automated) | `/audit-claude-md` |
| After audit flags issues | `/fix-skills` or `/fix-claude-md` (manual) |
| When something new is needed | `/check-for-skills` |
| Lost track of what exists | `/system-map` |
