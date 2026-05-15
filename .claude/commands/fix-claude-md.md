Fix structural issues in CLAUDE.md files identified by `/audit-claude-md`.

## Usage
Run after `/audit-claude-md`. Specify which file to fix, or fix all files with issues.

## Process

1. **Identify files to fix**
   - Use findings from the most recent `/audit-claude-md` run
   - If called directly without prior audit, run `/audit-claude-md` first

2. **For each file to fix:**
   a. Read the current file
   b. Read the audit findings
   c. Apply fixes:
      - Extract long reference content to `docs/` files and replace with a pointer
      - Update stale skill names or file paths
      - Add missing sections (Purpose, Integrations, Skills, Ongoing Role)
      - Trim content that doesn't belong in CLAUDE.md
   d. Show the proposed rewrite
   e. Ask for approval before saving

3. **After fixing:**
   - If content was extracted to a new doc file, confirm the new file is created
   - Re-run `/audit-claude-md` on the fixed file to confirm it passes

## Important
- The router pattern is the goal: CLAUDE.md should be short, clear, and point outward — not contain everything
- When extracting content to docs, create the doc file before removing content from CLAUDE.md
- Always show changes before writing

## Output format
Side-by-side or inline diff with commentary on what moved where and why.
