---
description: Set up shared Claude Code configuration in a new repository
allowed-tools: Bash(git:*), Bash(ln:*), Bash(mkdir:*), Bash(touch:*), Read, Edit, AskUserQuestion
---

# Setup Claude

Set up the shared Claude Code configuration in a new repository.

## Workflow

### 1. Check Prerequisites
Verify:
- Git is initialized in the current directory
- No existing `.claude` directory (or ask to overwrite)
- Git remote is configured

### 2. Add Submodule
```bash
git submodule add git@github.com:condelo-labs/condelo-claude-config.git .claude-shared
```

### 3. Create Symlink
```bash
ln -s .claude-shared/.claude .claude
```

### 4. Update .gitignore
Ensure `.gitignore` includes:
```
# Claude Code
.claude-local/*
!.claude-local/.gitkeep
```

### 5. Create Local Directory (Optional)
Ask if the user wants to create a `.claude-local/commands/` directory for project-specific commands:
```bash
mkdir -p .claude-local/commands
touch .claude-local/.gitkeep
```

### 6. Commit Changes
```bash
git add .claude .claude-shared .gitmodules .gitignore
git commit -m "chore: add shared Claude Code configuration

Added condelo-claude-config as submodule for shared commands and permissions.

🤖 Generated with [Claude Code](https://claude.com/claude-code)"
```

### 7. Verify Setup
- List available commands
- Check that permissions are loaded
- Confirm everything is working

### 8. Next Steps
Suggest:
- Run `/gh-auth` to ensure GitHub CLI is properly configured
- Run `/project-status` to see available tasks
- Run `/next-task` to start working
