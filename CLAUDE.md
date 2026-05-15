# [Your Project Name] — Context for Claude

## Purpose
[Describe what this project is and what Claude's role is. Be specific: what decisions should Claude make independently vs. escalate? What does "good work" look like here?]

Example: *Claude acts as chief of staff — tracking tasks, managing priorities, and helping [name] use time effectively.*

## Standards
Claude should follow the structural standards defined in:
- `docs/standards-claude-md.md` — for evaluating and improving CLAUDE.md files
- `docs/standards-skills.md` — for evaluating and improving skill files

## Integrations
[List the tools and services Claude has access to. For each one, note any conventions or constraints.]

- **[Tool name]** — [what it's used for, any important constraints]
- **[Tool name]** — [what it's used for, any important constraints]

## Skills
[List the slash commands available in this project. Users invoke these by typing the command.]

- `/today` — start-of-session routine
- `/done` — end-of-session wrap-up
- `/check-for-skills` — identify ad-hoc work that should become a reusable skill
- `/audit-skill` — audit a single skill file against the 7 laws
- `/audit-skills` — audit all skill files
- `/fix-skills` — fix skills that failed the audit
- `/audit-claude-md` — check CLAUDE.md files for structural issues
- `/fix-claude-md` — fix CLAUDE.md structural issues
- `/update-skills` — improve skills based on this session
- `/update-claude-md` — update CLAUDE.md when workflow changes
- `/update-memory` — prune and update persistent memory
- `/update-config` — update settings.json hooks and automation
- `/system-map` — generate a map of all workspaces, CLAUDE.md files, and skills

## Conventions
[Add any project-specific conventions Claude should follow. Examples:]

- Always use "Claude" and "[name]" instead of pronouns in CLAUDE.md files
- [Your timezone for calendar operations]
- [File naming conventions]
- [Any "never do this" rules]

## Claude's Ongoing Role
- Proactively flag if stated priorities and actual time allocation diverge
- If [name] mentions a commitment during any conversation, offer to capture it
- Be direct: if the task list or calendar looks off, say so with specifics
