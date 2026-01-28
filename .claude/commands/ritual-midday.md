# Midday Ritual: Condelo PoC Progress Check

You are running the Condelo PoC Midday Check-in. This is a quick 5-minute pulse check to ensure the day is on track.

## Context
- Reference the morning's One Win and Tiny Wins
- Check if we're on track or need to pivot
- Identify any blockers that emerged

## Your Tasks

### 1. Quick Status Check
```bash
# Check git activity today
git log --oneline --since="6am"

# Any uncommitted work?
git status --short

# Current branch
git branch --show-current
```

### 2. Progress Assessment
For each morning goal, assess:
- **One Win**: Started? In progress? Blocked? Done?
- **Tiny Wins**: How many completed?

### 3. Blocker Identification
If progress is slower than expected:
- What's the actual blocker?
- Is the scope creeping?
- Should we pivot to something more achievable?

### 4. Afternoon Adjustment
Based on progress, recommend:
- Continue current path, OR
- Adjust scope/approach, OR
- Switch to a different priority

## Output Format (follow exactly)

```
## ⏰ MIDDAY CHECK-IN

### Morning Goals Progress
| Goal | Status | Notes |
|------|--------|-------|
| One Win: [name] | 🔴/🟡/🟢 | ... |
| Tiny Win 1: [name] | ⬜/🟢 | ... |
| Tiny Win 2: [name] | ⬜/🟢 | ... |
| Tiny Win 3: [name] | ⬜/🟢 | ... |

### Commits Today
[List or "None yet"]

### Blockers
[List any, or "None identified"]

### Afternoon Plan
**Recommendation**: [Continue / Adjust / Pivot]

[If adjusting/pivoting, explain what and why]

**Afternoon focus**: [Specific goal for rest of day]
```

## Constraints
- Keep this quick (5 minutes max)
- Be honest about progress - it's okay to be behind
- If blocked, propose an unblock action
- Don't add new scope mid-day unless critical
