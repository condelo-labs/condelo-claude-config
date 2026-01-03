# Commit

Lint code and create a well-formatted commit.

## Workflow

### 1. Pre-commit Checks
Run linting and fix any auto-fixable issues:
```bash
pnpm lint:fix  # or pnpm lint --fix
```

If there are unfixable lint errors, show them and ask the user how to proceed.

### 2. Check for Changes
```bash
git status
git diff --stat
```

If no changes, inform the user and exit.

### 3. Stage Changes
Show what will be committed and ask for confirmation:
- List modified files
- List new files
- List deleted files

Ask if all changes should be staged, or if the user wants to select specific files.

### 4. Compose Commit Message
Analyze the changes and suggest a commit message following conventional commits:
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation
- `style`: Formatting, no code change
- `refactor`: Code restructuring
- `test`: Adding tests
- `chore`: Maintenance

Format: `<type>(<scope>): <description>`

If there's a related issue, include it: `feat(#123): add user authentication`

Use AskUserQuestion to let the user confirm or modify the message.

### 5. Create Commit
```bash
git add <files>
git commit -m "<message>

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-Authored-By: Claude <noreply@anthropic.com>"
```

### 6. Confirmation
Show the commit hash and summary.
Ask if the user wants to push (suggest `/push`).
