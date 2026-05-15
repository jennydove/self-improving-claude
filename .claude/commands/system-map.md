Generate a map of the current Claude setup: all active workspaces, CLAUDE.md files, and skills.

## When to run
- When onboarding someone new to the setup
- When you've lost track of what exists across workspaces
- Before running `/audit-skills` or `/audit-claude-md` to know the full scope
- Periodically as a health check on the system

## Process

1. **Find all CLAUDE.md files**
   - Search the file system for CLAUDE.md files across all active project directories
   - Note the path and one-line summary of each project's purpose

2. **Find all skill files**
   - List all `.md` files in `.claude/commands/` for each workspace
   - Note which workspace each skill belongs to

3. **Find all memory files**
   - Check `memory/MEMORY.md` for the current index
   - Note any memory files that exist but aren't in the index

4. **Produce the system map:**

```
Claude System Map — [date]

## Workspaces
[path/to/project]
  Purpose: [one-line from CLAUDE.md]
  CLAUDE.md: [PASS / NEEDS UPDATE / MISSING]
  Skills: [count]

[path/to/project]
  ...

## Skills by Workspace
[workspace name]
  - /skill-name — [one-line description]
  - /skill-name — [one-line description]

## Memory
  Index entries: [count]
  Memory files: [count]
  Stale entries (in index but file missing): [list or "none"]
  Orphaned files (file exists but not in index): [list or "none"]

## Health Summary
  Workspaces needing attention: [list or "none"]
  Skills needing audit: [list based on last audit scores, or "run /audit-skills"]
  Memory issues: [list or "none"]
```

5. **Flag anything that needs immediate attention**
   - CLAUDE.md files that reference skills that don't exist
   - Skills that are orphaned (file exists, not listed in any CLAUDE.md)
   - Memory index that's out of sync with actual files

## Output format
The structured map above, followed by a prioritized list of anything that needs attention. If everything is healthy, say so.
