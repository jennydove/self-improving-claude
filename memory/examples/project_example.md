---
name: Example project memory
description: Example of how to record a project decision or deadline
type: project
---

All non-critical merges are frozen from 2026-06-01 through the mobile release cut.

**Why:** Mobile team is cutting a release branch and needs a stable base. Legal flagged that any changes to auth middleware after freeze require additional review.

**How to apply:** Flag any PR work scheduled after 2026-06-01 as potentially blocked. Don't suggest merging non-critical changes during this window without noting the freeze.
