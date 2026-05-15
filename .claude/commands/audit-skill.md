Audit a single skill file against the 7 laws of great Claude skills.

## Usage
Run `/audit-skill` and specify which skill to audit, or paste the skill content directly.

## Process

1. **Read the skill file** from `.claude/commands/[skill-name].md`

2. **Score against the 7 laws** (see `docs/standards-skills.md` for the full rubric)
   - Score each law 1–5
   - Note specific line or section that fails if score < 4

3. **Produce a scored report:**

```
Skill: [name]
Overall: [X/35]

Law 1 – [Name]: [score]/5
  Issue: [specific problem, if any]

Law 2 – [Name]: [score]/5
  Issue: [specific problem, if any]

[... for all 7 laws]

Top 3 improvements:
1. [most impactful fix]
2. [second most impactful fix]
3. [third most impactful fix]
```

4. **Ask whether to run `/fix-skills` on this skill** if score < 28/35

## Output format
Structured report as above. Be specific — "the trigger description is too vague" is useful; "could be improved" is not.
