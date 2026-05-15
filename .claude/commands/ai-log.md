Write a brief activity log entry for the current session.

Run at the end of every session via `/done`. Skip only if the session was a single quick question with no changes made.

## Process

1. **Review the session** and draft a log entry covering:
   - What was built or changed (3–5 bullet points)
   - Key decisions made and why
   - Follow-ups identified (anything started but not finished)

2. **Write the entry** to `ai-log/YYYY-MM-DD — [Short description].md`
   - Create the `ai-log/` directory if it doesn't exist
   - If an entry already exists for today, append a section with a timestamp rather than overwriting

3. **Confirm** with the file path when done

## Output format

```markdown
# [Short description of session]
**Date:** YYYY-MM-DD

## What Was Built or Changed
- [bullet points]

## Key Decisions Made
- [decision]: [why]

## Follow-ups Identified
- [what's still open]
```

## Notes
- This step has no approval gate — write immediately
- Keep entries short enough to scan in 30 seconds
- The value is in the accumulation over time, not any single entry
