---
description: Pick up next task from GitHub, plan, implement, and create PR
allowed-tools: Bash(git:*), Bash(gh:*), Bash(pnpm:*), Read, Edit, Write, Grep, Glob, TodoWrite, AskUserQuestion, Task
---

# Next Task

Pick up the next task from GitHub and work through to completion.

## Workflow

You MUST follow this workflow exactly, using ultrathink for all analysis:

### 1. Task Selection
- Fetch tasks from the GitHub project board that are in "Todo" status
- Present a prioritized list showing:
  - **Recommended next task** (based on priority, dependencies, and workflow continuity)
  - **Other high-priority tasks** that could be worked on
  - **Tasks that would improve developer experience**
- Use the AskUserQuestion tool with tabs format to let the user select which task to work on

### 2. Task Analysis & Planning
Once a task is selected:
- Analyze the task requirements thoroughly (ultrathink)
- Use AskUserQuestion with tabs format to clarify any ambiguities
- Present a detailed plan of attack including:
  - Files that will be modified/created
  - Key implementation decisions
  - Potential risks or considerations
- Ask if the user wants to proceed or make changes

### 3. Implementation
- Update the GitHub issue status to "In progress"
- Create a feature branch: `<issue-number>-<short-description>`
- Add a comment to the issue noting work has started
- Work through the implementation, prompting for input when needed
- Use TodoWrite to track progress on subtasks
- Run linting, type checking, and tests as you go

### 4. PR Creation
Before creating the PR:
- Run `pnpm lint` and fix any issues
- Run `pnpm typecheck` and fix any errors
- Run `pnpm test` and ensure tests pass
- Review the changes yourself (pre-PR checklist from CLAUDE.md if available)

Create the PR with:
- Clear title referencing the issue
- Summary of what was implemented
- Test plan
- Link to close the issue

### 5. Completion Report
Present a report including:
- What was implemented
- Key decisions made
- Any follow-up items identified
- The PR URL

Then wait for the user to get the PR reviewed by Copilot in GitHub.
Suggest running `/pr-fix` once Copilot review comments are available.

## GitHub Project Reference
If CLAUDE.md contains GitHub project IDs, use them for status updates.
