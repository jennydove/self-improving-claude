Run the end-of-session wrap-up routine.

This is an orchestrator — it calls a focused set of sub-skills in sequence. Each step is independent and can be run on its own if needed.

## Steps

1. **Log what was accomplished**
   - Summarize the work done this session in 3–5 bullet points
   - Note any decisions made and the reasoning behind them
   - Flag anything that was started but not finished

2. **Update memory** (`/update-memory`)
   - Review the session for anything worth persisting
   - New feedback or corrections from the user
   - Project state changes, decisions, deadlines
   - New external references discovered

3. **Check for new skills** (`/check-for-skills`)
   - Review ad-hoc work done this session
   - Identify anything that was done manually that should become a reusable slash command
   - If found, draft the skill and ask the user whether to save it

4. **Update skills if needed** (`/update-skills`)
   - If any existing skills were used and felt off or produced suboptimal output, flag them
   - Suggest specific improvements

5. **Push config to GitHub** (if syncing)
   - If this project has a GitHub sync configured, push the latest config
   - Skip if no sync is configured

## Output format
Concise wrap-up. The session log is the most important output — make it clear enough that the next session can start without re-reading the conversation.

## Why sub-skills instead of one big command?
Each step here is independent. You can run `/update-memory` mid-session without running the full wrap-up. You can skip `/check-for-skills` on short sessions. Breaking the routine into sub-skills makes each piece debuggable, updatable, and reusable on its own.
