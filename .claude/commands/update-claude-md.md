Update CLAUDE.md when the workflow, integrations, or skill list has changed.

## When to run
- When a new skill is added or an existing one is renamed/removed
- When integrations change (new tools added, old ones removed)
- When Claude's ongoing role or responsibilities shift
- When conventions are established or changed

## Process

1. **Identify what changed this session**
   - New skills created (from `/check-for-skills`)
   - Skills removed or renamed
   - New integrations or tools
   - New conventions established
   - Shifts in how Claude should approach work here

2. **Read the current CLAUDE.md**

3. **Propose specific updates:**
   - Add new skills to the Skills section with correct invocation syntax
   - Remove or rename any stale skill references
   - Update integrations section
   - Update conventions if new ones were established
   - Update Claude's ongoing role if responsibilities changed

4. **Show proposed changes** and ask for approval before writing

## Important
- CLAUDE.md should stay short and pointed — if an update would make it significantly longer, consider whether the content belongs in a `docs/` file instead
- Never add content to CLAUDE.md that should live in memory (ephemeral project state, decisions)
- Skill names in CLAUDE.md must match the actual filenames in `.claude/commands/`
