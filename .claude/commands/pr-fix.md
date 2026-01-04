---
description: Review and implement Copilot review feedback on current PR
allowed-tools: Bash(git:*), Bash(gh:*), Read, Edit, Write, Grep, Glob, TodoWrite, AskUserQuestion
---

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

When addressing review comments, you MUST both reply AND resolve the thread.

### Prerequisites: Install gh-pr-review extension
The `gh-pr-review` extension provides simple commands for thread management:
```bash
gh extension install agynio/gh-pr-review
```

### 1. List unresolved threads
```bash
gh pr-review threads list --unresolved -R {owner}/{repo} {pr_number}
```

Returns JSON array with thread metadata including `threadId`, `path`, `line`, and `isResolved`.

### 2. Reply to the comment
```bash
gh api repos/{owner}/{repo}/pulls/{pr}/comments/{comment_id}/replies -f body="Fixed in <commit-sha>"
```

### 3. Resolve the thread
```bash
gh pr-review threads resolve --thread-id {thread_id} -R {owner}/{repo} {pr_number}
```

### Workflow Pattern
1. Fetch all unresolved threads with `gh pr-review threads list --unresolved`
2. For each comment you address:
   - Reply to the comment with the fix location
   - Match the comment to its thread by `path` and `line`
   - Resolve the thread using `gh pr-review threads resolve`

### Fallback: GraphQL (if extension unavailable)
If the extension isn't available, use GraphQL directly:
```bash
# List threads
gh api graphql -f query='
  query($owner: String!, $repo: String!, $pr: Int!) {
    repository(owner: $owner, name: $repo) {
      pullRequest(number: $pr) {
        reviewThreads(first: 100) {
          nodes { id isResolved path line comments(first: 1) { nodes { databaseId body } } }
        }
      }
    }
  }
' -f owner='{owner}' -f repo='{repo}' -F pr={pr_number}

# Resolve a thread
gh api graphql -f query='
  mutation($threadId: ID!) {
    resolveReviewThread(input: {threadId: $threadId}) {
      thread { isResolved }
    }
  }
' -f threadId='{thread_node_id}'
```
