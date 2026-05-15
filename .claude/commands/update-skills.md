Review skills that were used or referenced this session and suggest improvements based on what actually happened.

## When to run
- Called automatically as part of `/done`
- Run manually any time a skill produced suboptimal output

## Process

1. **Identify skills used this session**
   - Which slash commands were invoked?
   - Were any skills referenced even if not formally invoked?

2. **For each skill used, ask:**
   - Did it produce the right output format?
   - Did it miss any steps that were needed?
   - Did it include steps that weren't useful?
   - Were there any instructions that were ambiguous or misinterpreted?
   - Did the user correct or redirect anything mid-skill?

3. **For each skill with an issue:**
   - Describe the specific problem
   - Propose a concrete fix (show the change, not just describe it)
   - Ask the user whether to apply it

4. **Apply approved changes** and confirm saves

## Output format
Only surface issues worth fixing — don't manufacture problems. If a skill worked well, say so briefly and move on. For issues, be specific: "step 3 should include X" not "could be clearer."
