# Check CI

Quick check of CI status for the current branch or PR.

## Workflow

### 1. Identify Context
- Get current branch name
- Check if there's an open PR for this branch

### 2. Check PR Status (if PR exists)
```bash
gh pr checks <pr-number>
```

Display in a clear format:
- ✅ Passing checks
- ❌ Failing checks
- ⏳ Pending checks

### 3. Check Latest Workflow Run (if no PR)
```bash
gh run list --branch <branch> --limit 1
gh run view <run-id>
```

### 4. If Failures Exist
For each failing check:
- Show the check name and status
- Offer to view logs: `gh run view <run-id> --log-failed`
- Suggest potential fixes based on the failure type

### 5. Summary
Provide a quick summary:
- Overall status (passing/failing/pending)
- Time since last run
- Suggest next action (wait, fix issues, or proceed)
