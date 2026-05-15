# Standards: Healthy CLAUDE.md Files

Use this rubric when running `/audit-claude-md`. A CLAUDE.md file exists to give Claude project-specific context — not to be a comprehensive reference document.

---

## The Router Pattern

The most important principle: **CLAUDE.md is a router, not a reference.**

It should be short enough to read in 60 seconds, point outward to detailed docs rather than contain them, and stay accurate over time because it changes rarely.

A CLAUDE.md file that is long, dense, or full of detailed conventions is a sign that content has accumulated that belongs in `docs/` files.

---

## Required Sections

### Purpose
One paragraph. What is this project? What is Claude's role here specifically? What decisions should Claude make independently vs. escalate?

**Failure mode:** Missing entirely, or so generic it could apply to any project.

### Integrations
A list of tools and services Claude has access to in this project. For each: what it's used for, and any important constraints or conventions.

**Failure mode:** Missing tools, no constraints noted, or a wall of text explaining how each tool works (that belongs in a `docs/` reference file).

### Skills
A list of all slash commands available in this project with a one-line description of each. Names must match actual filenames in `.claude/commands/`.

**Failure mode:** Skills list is out of date (references renamed or deleted files), descriptions are missing, invocation syntax is wrong.

### Claude's Ongoing Role
Specific, recurring behaviors Claude should maintain throughout any conversation in this project — not just during skill runs.

**Failure mode:** Generic ("be helpful"), missing, or describes one-time setup rather than ongoing behavior.

---

## Structural Rules

### Point, don't embed
If you find yourself writing more than 3–4 sentences about a convention or reference, it belongs in `docs/`. Put a pointer in CLAUDE.md instead:
```
See `docs/naming-conventions.md` for file naming rules.
```

### Keep it current
The skills list and integrations section drift fastest. After adding or renaming a skill, run `/update-claude-md` to keep the list accurate.

### Use the pronoun convention
CLAUDE.md files should use names ("Claude", "[user's name]") instead of pronouns ("I", "you", "me") to avoid ambiguity about who each instruction refers to.

### No ephemeral content
CLAUDE.md is not the place for current project state, in-progress work, or temporary decisions. That belongs in memory files. CLAUDE.md should be stable and accurate for months at a time.

---

## Audit Checklist

- [ ] File is short enough to read in 60 seconds
- [ ] Has a clear Purpose section specific to this project
- [ ] Lists integrations with constraints
- [ ] Lists all active skills with correct names
- [ ] Defines Claude's ongoing role specifically
- [ ] No long reference content (points to `docs/` instead)
- [ ] No ephemeral project state
- [ ] Skill names match actual files in `.claude/commands/`
- [ ] Uses names instead of pronouns
