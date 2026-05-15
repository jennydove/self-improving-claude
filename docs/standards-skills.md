# Standards: Great Claude Skills

The 7 laws of great Claude skills, based on Aakash Gupta's research from 75 tests:
[Claude Skills: The 7 Laws from 75 Tests](https://www.aibyaakash.com/p/claude-skills-7-laws)

Use this rubric when running `/audit-skill` or `/audit-skills`. Score each law 1–5.

---

## The 7 Laws

### Law 1: Clear Trigger
The skill has an unambiguous description of when it should be invoked. Claude and the user should both know exactly when this skill applies — and when it doesn't.

**Signs of failure:** Trigger is too broad ("use when working on tasks"), overlaps with other skills, or is missing entirely.

**Score 5:** A single sentence that precisely defines when and why to invoke this skill, with any explicit exclusions noted.

---

### Law 2: Single Responsibility
The skill does one thing. If you can't summarize what it does in one sentence without using "and," it's doing too much.

**Signs of failure:** The skill combines multiple unrelated operations, or the output covers too many different concerns.

**Score 5:** One clear job. If the skill needs to do multiple things, it orchestrates sub-skills rather than doing everything itself.

---

### Law 3: Explicit Output Format
The skill defines exactly what the output should look like — format, structure, length, and level of detail.

**Signs of failure:** Output format is left to Claude's discretion, produces inconsistent results across runs, or is described vaguely ("provide a summary").

**Score 5:** Output format is specified with examples or templates. The user knows exactly what they'll get before they run it.

---

### Law 4: Concrete Steps
The skill's process is described as specific, executable steps — not vague goals.

**Signs of failure:** Steps say "review X" or "consider Y" without explaining what reviewing or considering means. Steps are too high-level to be actionable.

**Score 5:** Each step describes what to do, what to look for, and what to produce. Someone reading the steps for the first time could follow them without guessing.

---

### Law 5: Handles Edge Cases
The skill anticipates what to do when the normal path doesn't apply.

**Signs of failure:** The skill breaks or produces bad output when inputs are missing, empty, or unusual. No guidance on what to do when preconditions aren't met.

**Score 5:** Explicitly addresses at least the most common edge cases (empty input, missing files, ambiguous user intent).

---

### Law 6: Appropriate Scope
The skill is neither too narrow (so specific it rarely runs) nor too broad (so general it's always incomplete). It matches the actual recurring need.

**Signs of failure:** The skill has never been run because the trigger situation is too rare. Or it's run frequently but always needs significant manual follow-up because it under-delivers.

**Score 5:** Scope matches the actual recurring use case. Runs as-is without needing significant customization each time.

---

### Law 7: Self-Contained
The skill has everything Claude needs to run it — context, standards, format, constraints. It doesn't rely on Claude remembering things from previous sessions or on the user providing setup instructions each time.

**Signs of failure:** The skill references standards or context that aren't available (e.g., "follow the usual format" without defining it, or "check the project doc" without a path).

**Score 5:** Everything Claude needs is in the skill file or in a clearly referenced, stable document. The skill works the same way regardless of what else happened in the session.

---

## Scoring Guide

| Total Score | Interpretation |
|---|---|
| 33–35 | Excellent — ship it |
| 28–32 | Good — minor improvements worth making |
| 21–27 | Needs work — one or two laws are significantly failing |
| < 21 | Rewrite — fundamental issues with structure or scope |

Threshold for `/fix-skills`: any skill scoring below 28/35.
