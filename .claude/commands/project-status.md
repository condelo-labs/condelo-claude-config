---
description: Overview of GitHub project board and task status
allowed-tools: Bash(gh:*), AskUserQuestion
---

# Project Status

Overview of the GitHub project board and task status.

## Workflow

### 1. Fetch Project Data
Use the GitHub CLI to fetch project items:
```bash
gh project item-list <project-number> --owner <owner>
```

### 2. Categorize Tasks
Group tasks by status:
- **In Progress**: Currently being worked on
- **Todo**: Ready to be picked up
- **Done**: Recently completed

### 3. Display Summary

```
## Project: <Project Name>

### 🔄 In Progress (X items)
| # | Title | Priority | Assignee |
|---|-------|----------|----------|
| 1 | Task description | P0 | @user |

### 📋 Todo (X items)
| # | Title | Priority | Size |
|---|-------|----------|------|
| 2 | Task description | P1 | M |

### ✅ Recently Done (last 5)
| # | Title | Completed |
|---|-------|-----------|
| 3 | Task description | 2 days ago |
```

### 4. Recommendations
Based on the project state, suggest:
- Which task to pick up next (highest priority Todo)
- Any blockers or dependencies to be aware of
- Tasks that have been in progress too long

### 5. Quick Actions
Offer quick actions using AskUserQuestion:
- Start working on a specific task (`/next-task`)
- Check CI for in-progress items (`/check-ci`)
- View details of a specific issue
