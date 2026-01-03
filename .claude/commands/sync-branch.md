# Sync Branch

Synchronize the current branch with main.

## Workflow

### 1. Check Current State
- Identify current branch
- Check for uncommitted changes
- If changes exist, ask user whether to stash, commit, or abort

### 2. Fetch Latest
```bash
git fetch origin main
```

### 3. Choose Sync Method
Ask the user (using AskUserQuestion with tabs):
- **Rebase** (Recommended): Cleaner history, replays your commits on top of main
- **Merge**: Creates a merge commit, preserves original commit order

### 4. Execute Sync
For rebase:
```bash
git rebase origin/main
```

For merge:
```bash
git merge origin/main
```

### 5. Handle Conflicts
If conflicts occur:
- List conflicting files
- For each file, show the conflict and propose a resolution
- Use AskUserQuestion to confirm each resolution
- After resolving, continue the rebase/merge

### 6. Verify
- Run `pnpm typecheck` to ensure no type errors were introduced
- Run `pnpm test` to ensure tests still pass
- Report success and any issues found

### 7. Push (Optional)
Ask if the user wants to force-push the rebased branch:
```bash
git push --force-with-lease origin <branch>
```

Note: Only force-push if rebase was used. For merge, a normal push is sufficient.
