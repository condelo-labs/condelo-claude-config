# Evening Ritual: Condelo PoC Daily Wrap-up

You are running the Condelo PoC Evening Wrap-up. This captures the day's progress, updates project tracking, and sets up tomorrow.

## Context
- Close out the day's work cleanly
- Update GitHub project status
- Capture learnings and blockers
- Prime tomorrow's planning

## Your Tasks

### 1. Day Summary
```bash
# All commits today
git log --oneline --since="6am" --format="%h %s"

# Files changed today
git diff --stat $(git log --since="6am" --format="%H" | tail -1)^..HEAD 2>/dev/null || echo "No commits today"

# Any open PRs
gh pr list --state open --author @me

# Current branch status
git status --short
```

### 2. Goal Assessment
Compare actual progress against morning goals:
- One Win: Achieved? Partial? Missed?
- Tiny Wins: How many completed?
- Unexpected work: What came up that wasn't planned?

### 3. GitHub Project Update
If issues were completed or status changed:
```bash
# List current project items
gh project item-list 3 --owner sharpworks --limit 20
```

Recommend any status updates needed.

### 4. Blockers & Learnings
- What blocked progress today?
- What took longer than expected?
- What would you do differently?
- Any patterns added to CLAUDE.md?

### 5. Tomorrow Setup
- What should tomorrow's One Win be?
- Any prep work to do tonight?
- Any meetings/deadlines tomorrow?

## Output Format (follow exactly)

```
## 🌙 END OF DAY WRAP-UP

### 📊 Today's Scorecard
| Goal | Result | Notes |
|------|--------|-------|
| One Win | ✅/⚠️/❌ | ... |
| Tiny Wins | X/Y completed | ... |

### 📝 Commits Today
[List with short descriptions]

### 🔀 Open PRs
[List with status, or "None"]

### 🚧 Blockers Encountered
[List, or "None"]

### 💡 Learnings
- [What you learned or would do differently]

### 📋 GitHub Project Updates Needed
[List any status changes to make, or "None needed"]

### 🌅 TOMORROW'S SETUP

**Suggested One Win**: [Specific deliverable]

**Prep for tomorrow**: [Any actions to take tonight, or "None needed"]

**Days remaining**:
- Atom Bank (Feb 6): X days
- Full PoC (Feb 28): X days
```

### 6. Clean Exit Checklist
Before signing off, verify:
- [ ] All work committed (or stashed with clear message)
- [ ] No broken builds on current branch
- [ ] PR created if work is ready for review
- [ ] Tomorrow's context captured

## Constraints
- Be honest about what was/wasn't achieved
- Don't guilt-trip about missed goals - just capture and move on
- Focus on actionable learnings
- Keep tomorrow's One Win realistic based on today's pace
