Review what happened this session and identify whether any ad-hoc work should become a reusable slash command.

## When to run
- At the end of any session where Claude did something new or multi-step
- Any time the user says "let's do that again" or "I do this every week"
- Automatically called as part of `/done`

## Process

1. **Review the session**
   - What multi-step tasks did Claude perform?
   - What did the user ask Claude to figure out or research?
   - Were there any sequences of tool calls that solved a recurring problem?

2. **Apply the "would I do this again?" test**
   - If the answer is yes, it's a skill candidate
   - One-off tasks don't need skills; recurring tasks do

3. **For each candidate skill:**
   - Draft a name (verb + noun, e.g., `generate-weekly-report`)
   - Write a one-sentence trigger description
   - Sketch the steps as a command file
   - Present to the user for approval before saving

4. **Save approved skills**
   - Write to `.claude/commands/[skill-name].md`
   - Add to the skills list in `CLAUDE.md`

## Output format
- List skill candidates clearly with a short description of what each would do
- Draft the command file for any the user approves
- Don't create skills for things that were clearly one-time or highly context-specific
