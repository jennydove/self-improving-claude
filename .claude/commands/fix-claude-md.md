Fix structural issues in CLAUDE.md files identified by `/audit-claude-md`.

## Usage
Run after `/audit-claude-md`. Specify which file to fix, or fix all files with issues.

## Process

1. **Identify files to fix**
   - Use findings from the most recent `/audit-claude-md` run
   - If called directly without prior audit, run `/audit-claude-md` first

2. **Read `docs/standards-claude-md.md`** to understand the target structure

3. **For each file to fix:**
   a. Read the current file
   b. Read the audit findings
   c. Apply fixes based on the standards and audit findings
   d. Present the proposed rewrite in this format:

```
### [file path]
**Issues addressed:** [list from audit]

**Current** (relevant section):
[old text]

**Proposed:**
[new text]

**What moved where:** [if content was extracted to docs/]
```

   e. Ask for approval before saving

4. **After fixing:**
   - If content was extracted to a new doc file, create the doc file first, then update CLAUDE.md
   - Re-run `/audit-claude-md` on the fixed file to confirm it passes

## Edge cases
- If no audit findings exist, run `/audit-claude-md` first
- If CLAUDE.md doesn't exist, flag it and ask whether to create one from the template
- When extracting content to docs, create the doc file before removing content from CLAUDE.md
