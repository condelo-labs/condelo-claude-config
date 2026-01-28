# Morning Ritual: Condelo PoC Daily Planning

You are running the Condelo PoC Morning Ritual. This is a focused planning session to set up the day for maximum progress.

## Context (fixed - do not drift)
- **Project**: Condelo — AI-driven knowledge ingestion platform PoC
- **Today's date**: Use current date from system
- **Critical deadline #1**: Atom Bank meeting **Fri 6 Feb 2026**
  - Goal: Credible live demo + backup video recording + 1-page leave-behind
- **Critical deadline #2**: Full demoable PoC **Sat 28 Feb 2026**

## Demo Spine (what must work flawlessly for Feb 6)
1. User adds a Source (Google Drive CSV folder via service account)
2. System samples CSVs and stores a `source_sample`
3. Feeds Agent analyzes sample (GPT-4o JSON mode) → classification, recommendedLocation, confidence, summary
4. UI shows: /sources (list), /sources/new (form), /sources/:id (analysis + sample + re-analyse + logs)

## Your Tasks

### 1. Calculate Timeline
- Days remaining to Feb 6 (Atom Bank)
- Days remaining to Feb 28 (full PoC)
- Working days remaining (exclude weekends)

### 2. Assess Current State
Run these commands to gather project status:
```bash
# Get open issues and their status
gh project item-list 3 --owner sharpworks --format json | jq '.items[] | {title: .title, status: .status}'

# Check current branch and any uncommitted work
git status
git branch --show-current

# Check if there's an open PR
gh pr list --state open
```

### 3. Demo Spine Health Check
Test the core demo flow by checking:
- [ ] API health: `curl http://localhost:3001/health`
- [ ] Can list sources: `curl http://localhost:3001/sources`
- [ ] Web app loads: http://localhost:3000
- [ ] Docker services running: `docker compose ps`

Rate as **Red/Amber/Green**:
- **Green**: Full flow works end-to-end, demo-ready
- **Amber**: Flow works but has rough edges or missing polish
- **Red**: Critical path broken, blocking demo

### 4. Identify Focus Areas
Based on the assessment, identify:
- **Biggest Bottleneck**: Single thing most blocking demo readiness
- **Today's One Win**: One shippable deliverable (must be completable today)
- **Tiny Wins**: 2-3 tasks under 30 mins each that reduce demo risk

### 5. Risk Assessment
List top 3 risks to the Feb 6 meeting with concrete mitigations.

### 6. Rehearsal Script
Provide exact steps for a 10-minute demo rehearsal the user can run today.

## Output Format (follow exactly)

```
## 📅 DATE & COUNTDOWN
- Today: [date]
- Days to Atom Bank (Feb 6): X days (Y working days)
- Days to Full PoC (Feb 28): X days (Y working days)

## 📊 PROJECT STATUS
| Area | Status | Evidence |
|------|--------|----------|
| Core API | ✅/⚠️/❌ | ... |
| Web UI | ✅/⚠️/❌ | ... |
| Feeds Agent | ✅/⚠️/❌ | ... |
| Demo Polish | ✅/⚠️/❌ | ... |
| Documentation | ✅/⚠️/❌ | ... |

Open PRs: [list any]
Current branch: [branch]
Uncommitted work: [yes/no]

## 🚦 DEMO SPINE HEALTH: [RED/AMBER/GREEN]
[Reason for rating]

## 🎯 TODAY'S FOCUS

### One Win (Definition of Done)
[Specific deliverable with clear completion criteria]

### Tiny Wins (<30 min each)
1. [Task] — DoD: [criteria]
2. [Task] — DoD: [criteria]
3. [Task] — DoD: [criteria]

## ⚠️ RISKS TO FEB 6
| Risk | Likelihood | Impact | Mitigation |
|------|------------|--------|------------|
| ... | High/Med/Low | High/Med/Low | ... |

## 🎬 10-MINUTE REHEARSAL SCRIPT
1. [Step with expected outcome]
2. [Step with expected outcome]
...

## ❓ QUESTIONS (max 2, only if blocking)
[Any critical questions, or "None - ready to proceed"]
```

## Constraints
- Do NOT ask many questions; make best-effort assumptions and label them
- Focus on demo readiness, not perfection
- Prefer working software over comprehensive documentation
- If blocked, identify the unblock action, don't spiral
