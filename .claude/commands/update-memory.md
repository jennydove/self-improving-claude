Review the current session and update the persistent memory system.

## When to run
- Called automatically as part of `/done`
- Run manually any time something important happens mid-session

## Process

1. **Review the session for memory-worthy content**

   Save to memory when:
   - The user corrects an approach ("don't do X", "stop doing Y")
   - The user confirms a non-obvious approach worked ("yes exactly", "keep doing that")
   - Project state changes (new decisions, deadlines, stakeholder info)
   - New external references are discovered (where things live, who owns what)
   - User preferences or constraints are revealed

   Do NOT save to memory:
   - Code patterns or architecture (derivable from the codebase)
   - Ephemeral task details or in-progress work
   - Things already in CLAUDE.md
   - Git history or recent changes

2. **Check MEMORY.md** for existing entries that should be updated or removed
   - Is any existing memory stale or contradicted by this session?
   - Should any entry be merged with a new one?

3. **Write new memory files** for anything worth persisting
   - Each memory gets its own file with the correct frontmatter
   - File naming: `[type]_[topic].md` (e.g., `feedback_meeting_format.md`)

4. **Update MEMORY.md index** to include new entries and remove stale ones
   - Keep entries under 150 characters each
   - Keep the total index under 200 lines

## Memory file format
```markdown
---
name: [memory name]
description: [one-line description — used to decide relevance in future sessions]
type: [user | feedback | project | reference]
---

[memory content]
For feedback/project types: lead with the rule/fact, then **Why:** and **How to apply:** lines
```
