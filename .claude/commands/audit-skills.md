Audit all skill files in `.claude/commands/` against the 7 laws of great Claude skills.

## Process

1. **List all skill files** in `.claude/commands/`

2. **Score each skill** against the 7 laws (see `docs/standards-skills.md`)
   - Use the same rubric as `/audit-skill`
   - Score each law 1–5 per skill

3. **Produce a summary table:**

```
Skill Audit — [date]

| Skill | Score | Lowest Law | Top Issue |
|-------|-------|------------|-----------|
| skill-name | 28/35 | Law 3 | trigger too broad |
| skill-name | 22/35 | Law 1 | no clear output format |
...

Skills needing attention (< 28/35):
- [skill]: [top issue]
- [skill]: [top issue]
```

4. **Recommend next steps**
   - List skills to fix in priority order (lowest score first)
   - Offer to run `/fix-skills` on the worst offenders

## Notes
- This command is designed to run on a schedule (weekly or bi-weekly)
- See `docs/standards-skills.md` for the full 7-law rubric and scoring guide
- See README for the automation playbook — schedule this command first, before automating fixes
