# Self-Improving Claude

A system for building a Claude Code setup that gets better over time — not just a collection of slash commands, but a feedback loop that audits its own quality, fixes drift, and accumulates knowledge across sessions.

Built for product managers and operators who work with Claude daily and want a setup that meets and maintains their standards.

---

## The Problem

Most Claude setups are static. You write some instructions, maybe a few slash commands, and they slowly drift out of sync with how you actually work. Claude forgets what you decided last session. Skills grow inconsistent. CLAUDE.md files become stale. Every session starts slightly worse than the last.

## The Solution: A Self-Improving Flywheel

```
Do work
   ↓
Audit quality  ←──────────────┐
   ↓                          │
Fix issues                    │
   ↓                          │
Update memory + skills        │
   ↓                          │
Start next session ───────────┘
```

This repo gives you the scaffolding for that loop. Fork it, fill in your standards, and run the cycle.

---

## How It All Connects

There are two distinct rhythms in this system. Understanding the difference between them is the key to making it work.

### The session loop — runs every time you work with Claude

Every session starts with `/today` and ends with `/done`. These are orchestrators: each one calls a series of focused sub-skills in sequence.

`/done` is where the micro self-improvement happens. At the end of every session, Claude logs what was accomplished, updates persistent memory with anything new, checks whether any ad-hoc work should become a reusable skill, and flags improvements to existing skills. These are small, incremental updates — the system getting 1% better each time.

```
/today
  └── surface priorities, open tasks, flags

... do your work ...

/done
  ├── log what happened
  ├── update memory
  ├── check for new skills to create
  └── flag skill improvements
```

### The quality loop — runs on a slower cadence (weekly / bi-weekly)

Separate from the daily session loop, audits run on a schedule to check that the system itself is still at standard. Are the skill files well-structured? Is CLAUDE.md accurate and clean? Has anything drifted?

This is a macro check — not "what happened today" but "is the system healthy." It runs on a slower cadence because it's checking accumulated drift, not session-level changes.

```
/audit-skills        ← weekly
/audit-claude-md     ← bi-weekly

  └── findings → /fix-skills or /fix-claude-md (manual, you review first)
```

### Why two loops instead of one?

The session loop is fast and lightweight — it runs every time, so it has to be. It catches things that just happened.

The quality loop is thorough and slower — it checks everything against your standards, not just what changed today. Running it every session would be noisy and expensive. Running it never means drift goes undetected.

Together they compound: the session loop keeps Claude current, the quality loop keeps the system at standard.

---

## The Four Layers

### 1. Standards
Documents that define what "good" looks like for your setup. These live in `docs/` and are referenced by your CLAUDE.md and audit commands.

- `docs/standards-claude-md.md` — what a healthy CLAUDE.md looks like
- `docs/standards-skills.md` — what a well-structured skill looks like

### 2. Audits
Commands that check your setup against your standards and surface what's drifted.

| Command            | What it checks                                |
| ------------------ | --------------------------------------------- |
| `/audit-skill`     | A single skill file against the standards     |
| `/audit-skills`    | All skill files at once against the standards |
| `/audit-claude-md` | Your CLAUDE.md files against the standards    |

### 3. Fixes + Updates
Commands that act on audit findings and keep the system current.

| Command | What it does |
|---|---|
| `/fix-skills` | Rewrites skills that failed the audit |
| `/fix-claude-md` | Fixes structural issues in CLAUDE.md |
| `/update-skills` | Improves skills based on what happened this session |
| `/update-claude-md` | Updates CLAUDE.md when your workflow changes |
| `/update-memory` | Prunes and updates persistent memory |
| `/update-config` | Updates `settings.json` hooks and automation |

### 4. Growth
Commands that expand and map the system — not fixing what exists, but adding to it and understanding it.

| Command | What it does |
|---|---|
| `/check-for-skills` | Reviews the session and identifies ad-hoc work that should become a reusable skill |
| `/system-map` | Generates a full map of all workspaces, CLAUDE.md files, skills, and memory state |

---

## Session Commands

Two orchestrators bookend every working session. These are **not** monolithic commands — each one calls a set of focused sub-skills in sequence.

### Why sub-skills instead of one big command?

A monolithic `/done` command that does everything is fragile: it's hard to debug, hard to update one piece without breaking others, and hard to reuse any part of it independently. Sub-skills let you:
- Run just one step if that's all you need
- Update one piece without touching the others
- Understand at a glance what each step does
- Compose new commands from existing pieces

### `/today` — Start of session

Calls these sub-skills in sequence:

| Sub-skill | What it does |
|---|---|
| Pull config | If you have a GitHub sync, pulls the latest config before anything else |
| Surface priorities | Pulls today's tasks, flags anything due or overdue |
| Review open commitments | Scans memory for upcoming deadlines or flags |
| Set session context | Asks what you want to accomplish and notes any time constraints |

### `/done` — End of session

Calls these sub-skills in sequence:

| Sub-skill | What it does |
|---|---|
| Log session | Summarizes what was accomplished, decisions made, anything unfinished |
| `/update-memory` | Saves new feedback, project state, or references to persistent memory |
| `/check-for-skills` | Reviews ad-hoc work and asks: should any of this become a reusable skill? |
| `/update-skills` | Flags improvements to any skills that were used this session |
| Push config | If you have a GitHub sync, pushes the latest config |

Each sub-skill can also be run independently outside of `/done` — you don't have to run the full wrap-up to update memory mid-session, for example.

### `/check-for-skills`
The growth mechanism. Reviews what Claude did this session and asks: should any of this become a reusable slash command? Can be run mid-session or called automatically by `/done`.

### `/system-map`
Generates a full map of your Claude setup: all active workspaces, CLAUDE.md files, skills, and memory state. Run this when onboarding someone, before a major audit, or any time you've lost track of what exists across your workspaces.

---

## Memory System

The memory system is what makes improvement persist. Without it, audits and fixes are one-time events. With it, every session builds on the last.

### How it works

- `memory/MEMORY.md` — a concise index of all memory files (loaded into every session)
- `memory/*.md` — individual memory files, each covering one topic

### Memory types

| Type | What it stores |
|---|---|
| `user` | Who you are, your role, how you like to work |
| `feedback` | Corrections and confirmed approaches — what to repeat and what to avoid |
| `project` | Ongoing work, decisions, deadlines |
| `reference` | Where to find things in external systems |

### The rule

**MEMORY.md is an index, not a memory.** Each entry is one line pointing to a file. Memory content lives in the files. Keep MEMORY.md under 200 lines or it gets truncated.

---

## Automation Playbook

Automation should be turned on once you feel confident the system works for you. I recommend you follow this staged rollout:

### Stage 1: Manual everything (Week 1–2)
Run `/today`, `/done`, audits, and fixes by hand. Learn what they produce. Adjust your standards docs and skill files until the output feels right.

### Stage 2: Schedule audits (Week 3+)
Once audits are producing accurate, useful output, schedule them to run automatically. Use Claude Code's built-in `/schedule` skill:

```
/schedule  →  run /audit-skills every Monday morning
/schedule  →  run /audit-claude-md every two weeks
```

The fix commands stay manual. You review audit output and decide what to fix.

### Stage 3: Automate the full loop (when you trust it)
Only after the audit output has been consistently accurate for several weeks should you chain audits to fixes automatically. A noisy or inaccurate audit running fixes automatically will make things worse, not better.

---

## Quick Start

1. **Fork this repo**
2. **Edit `CLAUDE.md`** — fill in your actual project context, goals, and integrations (or use an existing one and add in the key pieces from this)
3. **Edit `docs/standards-claude-md.md`** — keep as-is or adapt
4. **Edit `docs/standards-skills.md`** — keep as-is or adapt
5. **Create your first memory files** — look at `memory/examples/` for the format
6. **Run `/today` to start a session, `/done` to end it**
7. **Run `/audit-skills` and `/audit-claude-md` after your first week**
8. **Schedule audits once output looks right**

---

## File Structure

```
/
├── README.md
├── CLAUDE.md                          # project instructions for Claude
├── .claude/
│   ├── settings.json                  # hooks + scheduled automation
│   └── commands/
│       ├── today.md                   # start-of-session orchestrator
│       ├── done.md                    # end-of-session orchestrator
│       ├── check-for-skills.md        # identify new skills from session work
│       ├── system-map.md              # map all workspaces, CLAUDE.md files, and skills
│       ├── audit-skill.md             # audit a single skill
│       ├── audit-skills.md            # audit all skills
│       ├── fix-skills.md              # fix skills that failed audit
│       ├── audit-claude-md.md         # audit CLAUDE.md files
│       ├── fix-claude-md.md           # fix CLAUDE.md structural issues
│       ├── update-skills.md           # improve skills from session learning
│       ├── update-claude-md.md        # update CLAUDE.md when workflow changes
│       ├── update-memory.md           # prune and update memory
│       └── update-config.md           # update settings.json and hooks
├── memory/
│   ├── MEMORY.md                      # index of all memory files
│   └── examples/
│       ├── feedback_example.md
│       ├── project_example.md
│       └── user_example.md
└── docs/
    ├── standards-claude-md.md         # what a healthy CLAUDE.md looks like
    ├── standards-skills.md            # the 7 laws of great Claude skills
    └── settings-guide.md              # hooks, scheduled triggers, automation playbook
```

---

## Credits

The Claude skills standards come from Aakash Gupta's research: [Claude Skills: The 7 Laws from 75 Tests](https://www.aibyaakash.com/p/claude-skills-7-laws).