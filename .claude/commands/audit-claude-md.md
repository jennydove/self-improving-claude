Audit CLAUDE.md files across this project against the structural standards in `docs/standards-claude-md.md`.

## Process

1. **Find all CLAUDE.md files** in the project (root and any subdirectories)

2. **For each CLAUDE.md, check:**
   - Does it follow the router pattern (concise, points to docs rather than containing everything)?
   - Does it have a clear Purpose section?
   - Does it list integrations with constraints noted?
   - Does it list all active skills with correct invocation syntax?
   - Does it define Claude's ongoing role clearly?
   - Is it free of content that belongs in a separate doc (long references, detailed conventions)?
   - Are file paths and skill names still accurate (not pointing to deleted files or renamed commands)?

3. **Produce a findings report:**

```
CLAUDE.md Audit — [date]

[file path]
  Status: [PASS / NEEDS WORK / FAIL]
  Issues:
    - [specific issue]
    - [specific issue]
  Recommendation: [what to fix]

[file path]
  ...

Summary: [N] files audited, [N] need attention
```

4. **Offer to run `/fix-claude-md`** on any file with issues

## Notes
- This command is designed to run on a schedule (bi-weekly or monthly)
- The most common failure modes: CLAUDE.md is too long, skills list is out of date, paths are wrong
- See `docs/standards-claude-md.md` for the full rubric
