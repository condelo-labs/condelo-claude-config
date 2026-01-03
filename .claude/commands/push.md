# Push

Lint, commit, and push changes to the remote repository.

## Workflow

### 1. Pre-push Checks
Run the full verification suite:
```bash
pnpm lint
pnpm typecheck
pnpm test
```

If any checks fail:
- Show the errors
- Ask if the user wants to fix them or push anyway (not recommended)

### 2. Check for Uncommitted Changes
If there are uncommitted changes:
- Run the `/commit` workflow first
- Or ask if changes should be stashed

### 3. Check Remote Status
```bash
git fetch origin
git status
```

Inform the user if:
- Branch is behind remote (needs pull/rebase)
- Branch is ahead of remote (ready to push)
- Branch has diverged (needs merge/rebase)

### 4. Push
```bash
git push -u origin <branch>
```

If the branch is new, this sets up tracking.

### 5. Post-push Actions
After successful push:
- Check if there's an open PR for this branch
- If no PR, ask if the user wants to create one
- If PR exists, show its status and any CI checks

### 6. Summary
Report:
- Commits pushed
- Branch status
- PR status (if applicable)
- Suggested next action
