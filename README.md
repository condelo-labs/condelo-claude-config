# Condelo Claude Code Configuration

Shared Claude Code configuration for Condelo projects. This repo provides reusable slash commands and permissions that can be used across multiple repos via git submodule.

## Quick Setup

To add this configuration to a new repo, run:

```bash
# Add as submodule
git submodule add git@github.com:condelo-labs/condelo-claude-config.git .claude-shared

# Create symlink to .claude directory
ln -s .claude-shared/.claude .claude

# Commit the changes
git add .claude .claude-shared .gitmodules
git commit -m "chore: add shared Claude Code configuration"
```

Or use the `/setup-claude` command if you already have Claude Code running.

## Updating

To pull the latest commands and configuration:

```bash
git submodule update --remote .claude-shared
git add .claude-shared
git commit -m "chore: update Claude Code configuration"
```

Or use the `/update-claude-config` command.

## Available Commands

| Command | Description |
|---------|-------------|
| `/next-task` | Pick up next task from GitHub, plan implementation, create PR |
| `/pr-fix` | Review and implement Copilot review feedback |
| `/sync-branch` | Rebase or merge current branch with main |
| `/check-ci` | Check CI status for current branch or PR |
| `/project-status` | Overview of GitHub project board |
| `/suggest` | Analyze repo and suggest improvements |
| `/commit` | Lint and commit with proper format |
| `/push` | Lint, commit, and push to remote |
| `/setup-claude` | Set up Claude config in a new repo |
| `/update-claude-config` | Pull latest shared config updates |
| `/gh-auth` | Ensure GitHub CLI has all required scopes |

## Project-Specific Commands

You can add project-specific commands by creating a `.claude-local/commands/` directory in your repo. These will be available alongside the shared commands.

## Permissions

The shared `settings.json` includes permissions for common development tools:
- Git operations (all commands)
- GitHub CLI (all commands)
- Package managers (pnpm, npm, yarn)
- File operations (non-destructive)
- Utilities (curl, sleep, timeout)

Destructive operations (rm, etc.) will still prompt for confirmation.
