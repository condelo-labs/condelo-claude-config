# Update Claude Config

Pull the latest shared Claude Code configuration.

## Workflow

### 1. Check Current Version
Read the current VERSION file:
```bash
cat .claude-shared/VERSION
```

### 2. Fetch Updates
```bash
cd .claude-shared
git fetch origin main
git log HEAD..origin/main --oneline
cd ..
```

### 3. Show Changes
If there are updates:
- Show the commits that will be pulled
- Show the CHANGELOG entries for new versions
- List new or modified commands

If no updates:
- Inform the user they're on the latest version
- Exit

### 4. Confirm Update
Use AskUserQuestion to confirm the update:
- Show what's new
- Ask if the user wants to proceed

### 5. Apply Update
```bash
git submodule update --remote .claude-shared
```

### 6. Commit the Update
```bash
git add .claude-shared
git commit -m "chore: update Claude Code configuration to v<version>

Changes:
<list of notable changes from CHANGELOG>

🤖 Generated with [Claude Code](https://claude.com/claude-code)"
```

### 7. Summary
Report:
- Previous version → New version
- New commands available
- Permission changes (if any)
- Suggest pushing the update
