# PR Fix

Review and address Copilot review comments on the current PR.

## Workflow

You MUST follow this workflow exactly, using ultrathink for all analysis:

### 1. Identify Current PR
- Determine the current branch
- Find the associated open PR
- If no PR exists, inform the user and suggest `/next-task`

### 2. Fetch Review Comments
- Use `gh api` to fetch all review comments on the PR
- Categorize comments by:
  - **Must fix**: Security issues, bugs, significant improvements
  - **Should fix**: Best practices, consistency, maintainability
  - **Consider**: Nice-to-haves, style preferences, over-engineering for current scope
  - **Skip**: Already addressed, not applicable, or would be over-engineering

### 3. Analysis & Decision
For each comment, ultrathink to determine:
- Is this a valid concern?
- Does fixing it align with project patterns (check CLAUDE.md)?
- Would it be over-engineering for the current scope (e.g., PoC)?

Present your analysis and get confirmation before proceeding.

### 4. Implementation
- Implement fixes for approved items
- Mark each comment as resolved in GitHub (if API supports it)
- Add comments explaining why certain items were skipped

### 5. Documentation
Update CLAUDE.md (or equivalent) with new learnings:
- Add new patterns to the "Code Quality Notes" section
- Document any new best practices discovered
- Add to the pre-PR checklist if applicable

### 6. Push & Report
- Run linting, type checking, and tests
- Commit with message: `fix(#<issue>): address Copilot review feedback`
- Push the changes
- Add a PR comment summarizing:
  - What was fixed
  - What was intentionally skipped and why
  - Any new patterns documented

### 7. Wait for Re-review
Inform the user the PR is ready for re-review.
Once merged, suggest running `/next-task` to continue with the next task.

## Comment Resolution
Try to resolve comments via the GitHub API:
```bash
gh api repos/{owner}/{repo}/pulls/{pr}/comments/{id}/replies -f body="Fixed in <commit>"
```
