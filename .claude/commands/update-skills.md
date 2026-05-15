Review skills that were used or referenced this session and suggest improvements.

Called automatically as part of `/done`, or run manually when a skill produced suboptimal output.

## Process

1. **Identify skills used this session**
   - Which slash commands were invoked?
   - Were any skills referenced even if not formally invoked?
   - If no skills were used this session, say so and stop

2. **Read each skill file and `docs/standards-skills.md`**

3. **For each skill used, check:**
   - Did it produce the expected output format?
   - Did it miss steps that were needed?
   - Did it include steps that weren't useful?
   - Were any instructions ambiguous or misinterpreted?
   - Did the user correct or redirect anything mid-skill?

4. **For each skill with an issue, present:**

```
### [skill-name]
**Problem:** [what went wrong or felt off]
**Proposed fix:**
[show the exact change — old text → new text, or the new section to add]
**Why:** [how this connects to the standards or the session experience]
```

5. **Apply approved changes** and confirm saves

## Edge cases
- If no skills were used, report that and exit
- If all skills worked well, say so briefly and move on
- If the user declines all suggestions, confirm no writes were made
