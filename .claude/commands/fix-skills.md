Fix skill files that failed the audit, based on findings from `/audit-skills`.

## Usage
Run after `/audit-skills`. Specify which skills to fix, or fix all skills below threshold.

## Process

1. **Identify skills to fix**
   - Use the findings from the most recent `/audit-skills` run
   - If called directly without a prior audit, run `/audit-skills` first

2. **Read `docs/standards-skills.md`** to understand what "good" looks like

3. **For each skill to fix:**
   a. Read the current skill file
   b. Read the audit findings for that skill
   c. Rewrite the skill addressing the top issues
   d. Show the diff and explain what changed and why
   e. Ask for approval before saving

4. **After all fixes:**
   - Re-run `/audit-skills [skill-name]` on each fixed skill to confirm scores improved
   - Update `CLAUDE.md` skills list if any skill names or descriptions changed

## Important
- Always show the proposed changes before writing them
- Never fix a skill that wasn't flagged by an audit without asking first
- If a skill's purpose has changed significantly, flag it — that's a rewrite, not a fix

## Output format
Per-skill diff with explanation. After all fixes, a brief summary of what changed across all skills.
