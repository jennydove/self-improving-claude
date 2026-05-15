Audit skill files in `.claude/commands/` against the standards defined in `docs/standards-skills.md`.

Run with a skill name to audit one, or run without arguments to audit all.

## Process

1. **Read `docs/standards-skills.md`** to load the current scoring rubric

2. **Identify skills to audit**
   - If a skill name was provided, audit just that one
   - Otherwise, list all `.md` files in `.claude/commands/` and audit each

3. **Score each skill** against the rubric in `docs/standards-skills.md`
   - Score each standard on the scale defined in the rubric
   - Note the specific line or section that fails for any low score

4. **Produce a report:**

For a single skill:
```
Skill: [name]
Overall: [score summary]

[Standard 1]: [score]
  Issue: [specific problem, if any]

[Standard 2]: [score]
  ...

Top 3 improvements:
1. [most impactful fix]
2. [second most impactful fix]
3. [third most impactful fix]
```

For all skills:
```
Skill Audit — [date]

| Skill | Score | Weakest Area | Top Issue |
|-------|-------|--------------|-----------|
| skill-name | [score] | [standard] | [issue] |
...

Skills needing attention:
- [skill]: [top issue]
```

5. **Recommend next steps**
   - Offer to run `/fix-skills` on skills below threshold
   - List fixes in priority order (lowest score first)

## Notes
- This command is designed to run on a schedule (weekly or bi-weekly)
- The scoring rubric lives in `docs/standards-skills.md` — update it there, not here
- See README for the automation playbook — schedule this command first, before automating fixes
